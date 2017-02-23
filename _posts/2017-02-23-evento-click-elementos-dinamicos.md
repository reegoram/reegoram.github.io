---
layout: post
title: Evento click para elementos generados dinámicamente vía jQuery
excerpt: Hace unos días me topé con un problema al tratar de disparar un evento click para un elemento generado dinámicamente vía jQuery. Es una web app, en la que necesito generar un botón para eliminar una fila de una tabla que genero vía jQuery. La solución que encontré, probé y funcionó te la presento a continuación.
categories: jQuery
---

Hace unos días me topé con un problema al tratar de disparar un evento click para un elemento generado dinámicamente vía jQuery. Es una web app, en la que necesito generar un botón para eliminar una fila de una tabla que genero vía jQuery. La solución que encontré, probé y funcionó te la presento a continuación.


En un archivo de html creo la estructura principal:
{% highlight html %}
<!DOCTYPE html>
<html lang="es">
  <head>
    <title></title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <script src="https://code.jquery.com/jquery-3.1.1.min.js" integrity="sha256-hVVnYaiADRTO2PzUGmuLJr8BLUSjGIZsDYGmIJLv2b8=" crossorigin="anonymous"></script>
    <script>
        //La función para generar la fila va aquí
    </script>
  </head>
  <body>
    <table>
        <tr>
            <td>Nombre</td>
            <td>Acción</td>
        </tr>
    </table>
  </body>
</html>
{% endhighlight%}

Y mediante un script de javascript le agrego la fila a la tabla con un botón para eliminarla:
{% highlight javascript %}
$(function(){
    //Generar fila
    $('table').append('<tr><td>Rigo :)</td><td><a href="javascript:void(0)" class="btnDelete">Eliminar</a></td></tr>');

    //Esta es la parte de código que le da funcionalidad al botón, en este caso, eliminar la fila
    $('table').on('click', 'a.btnDelete', function () {
        $(this).closest('tr').remove();
    });
});
{% endhighlight %}

Y quedaría de la siguiente manera:
<iframe height="auto" width="100%" src="../../demos/jQuery/remove-tr-dinamically.html"></iframe>

Puedes ver el código aquí en mi [repositorio de GitHub](https://github.com/{{site.author.github_username}}/reegoram.github.io/blob/master/demos/jQuery/remove-tr-dinamically.html "Demo @ Github repository"){:target="_blank"}