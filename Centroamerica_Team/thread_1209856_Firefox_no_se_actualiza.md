---
title: "Firefox no se actualiza"
date: 2009-07-10
forum: Centroamerica Team
---

### Post by Nugar on 2009-07-10
Hola todos,

Me esta sucediendo algo interesante. Cuando salio Firefox 3.5 final, Ubuntu no lo puso en los updates automaticamente, asi que lo instale independientemente.

Ahora que si salio, lo instalo mediante el updater y de todos modos cuando lo lanzo, me sale que es el 3.0.11 o algo asi.

Lo ideal para mi seria que se actualizara solo (aunque no tengo problemas con actualizarlo yo)

Alguna sugerencia?

Saludos,

Nugar

---

### Post by eivar on 2009-07-10
Hola Nugar, suena a que en tu computadora tienes las ambas veriones la vieja y la más nueva.

Cuentanos un poco más que fué lo que hiciste ya que por lo que escribes no me queda claro cual puede ser la causa del problema ni como es la "instalación manual" que hiciste.

Saludos.

---

### Post by Nugar on 2009-07-10
Hola Eivar,

Gracias por tu respuesta. El dia que salio Firefox, todavia no estaba disponible en el repositorio de Ubuntu, pero por supuesto que yo lo queria *"yamente"*

Asi que en lugar de esperar a que lo actualizaran en el repositorio y me avisaran mediante la estrellita que sale en el area donde estan los iconitos en la parte superior derecha (en la instalacion por defecto), me fui al sitio de firefox y baje el 3.5

Siguiendo las instrucciones, lo instale a ~/firefox/firefox y corre genial, pero desde ayer o anteayer, cada vez que hay una actualizacion en esa área del "tray" (no se como se llama en Gnome), me vuelv a aparecer firefox entre los programas a actualizar. Le doy ok, y supuestamente se actualiza, pero si corro el programa mediante el icono por defecto que viene con Ubuntu 9.04, lanza el firefox 3.0.11 y no el 3.5. Es decir que la actualización automatica con synaptic no esta instalando la version nueva.

A menos, claro, que la este instalando a mi directorio de usuario y este sobre escribiendo la que yo instale y no la que viene "de fabrica".

Al final, tengo dos instalaciones concurrentes de firefox, la 3.0.11 y la 3.5 y me sigue saliendo constantemente la 3.5 por actualizar.

Quizas lo ideal sería poder desactivar ese mensaje de actualizacion y encargarme de actualizar firefox por mi cuenta.

Saludos,

Humberto

---

### Post by eivar on 2009-07-13
Hola Nugar,

No estoy seguro que la actualización sea a la versión 3.5, en algun lugar leí que en Ubuntu seleccionan los paquetes que van a ir en cierta version y las actualizaciones son para cuestiones de seguridad o correciones en los paquetes.

Por favor toma una captura de pantalla de la ventana del actualizador y subela para ver el mensaje, también intenta actualizar usando el synaptic (Gestor de paquetes Synaptic) y nos cuentas que tal.


Saludos.

---

### Post by Nugar on 2009-07-13
Grcias eviar, voy a hacer en cuanto este frente a mi maquina y me salga el actualizador.
 
El actualizador en efecto habla de firefox 3.5, algo de branding y otra actualizacion del xul.  Las tres aparentan instalarse, pero al final queda todo igual y siguen apareciendo.
 
Saludos,
 
Nugar

---

### Post by gmunioz on 2009-07-15
Hola nug....:

1- Agrega a tu sources.list los siguientes repositorios, desde

synaptic o editando el archivo:

deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) jaunty main

deb-src [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) jaunty main

2- Desinstala:

- Borrando su directorio el firefox 3.5 descargado

desde su sitio

- Desde Synaptic Firefox 3.0.11 

3- En Synaptic, recarga y elige para instalar:

firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support

aplica, terminada la instalación cierra synaptic.

4- Pulsa con el botón derecho de mouse en Aplicaciones

elige Editar los menús - navega hasta Internet - 

 pulsa el botón derecho sobre Shiretoko -

elige propiedades, cambia Shiretoko Web Browser por Firefox

Cambia Firefox 3.5 beta por Web Browser

cierra.

5- Pulsa Aplicaciones - Internet - boton derecho sobre Firefox

elige Añadir este lanzador al panel.

Ya tienes el Firefox 3.5 incorporado y listo para recibir las

actualizaciones cuando estas estén disponibles.

---

### Post by Nugar on 2009-07-22
Hola gmunioz,

Gracias por tu post. Al principio lo hice y parecio no funcionar, luego lo repeti y ya estoy recibiendo correctamente las actualizaciones. 

En este momento, mi Help > About Shiretoko muestra version 3.5.2pre, Mozilla Firefox for Ubuntu canonical - 1.0

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.2pre) Gecko/20090721 Ubuntu/9.04 (jaunty) Shiretoko/3.5.2pre

Saludos,

Nugar

---

### Post by eivar on 2009-08-18
Hola Nugar,
gracias a tu post y las respuestas que te dieron sentí curiosidad probar el firefox-3.5 y descubrí que se puede tener instaladas sin problemas las versiones: 3.0.13 y 3.5.2 en jaunty simplemente instalando la última sin borrar la primera.

¿Por qué conservar la versión vieja?
Simplemente por dos razones: 
1. tengo muchos plugins y existen algunos que no tienen soporte para firefox3.5 (al menos por ahora)
2. hasta comprobar que todo va bien con la nueva versión.

NOTA: podemos instalar firefox 3.5 con el siguiente comando:
sudo aptitude install firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support

---

### Post by Nugar on 2009-08-19
Hola Eivar,

He notado una cosa y es que la mayoria de los plugins no funcionan en la version mas nueva porque sencillamente el autor les puso que son para la version tal y tal en el codigo.

Pero, hay un add on que se llama Nightly Tester Tools que habilita los add ons para la version que tengas.

Puedes bajarlo aqui: [https://addons.mozilla.org/en-US/firefox/addon/6543](https://addons.mozilla.org/en-US/firefox/addon/6543)

Saludos,

---

