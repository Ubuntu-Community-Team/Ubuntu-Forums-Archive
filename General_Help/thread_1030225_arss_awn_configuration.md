---
title: "arss awn configuration"
date: 2009-01-04
forum: General Help
---

### Post by Ant68 on 2009-01-04
Hello,
Could anyone let me know how to configure the aRSS applet in the Awn bar? Same for the Calendar applet? 

I would like to change the feeds?

Thanks,

---

### Post by Nautico on 2009-01-26
> **Ant68 said:**
> Hello,
Could anyone let me know how to configure the aRSS applet in the Awn bar? Same for the Calendar applet? 

I would like to change the feeds?

Thanks,



Quienes tenéis puesto en vuestro sistema la fantástica barra de tareas "Avant Window Navigator" habréis podido observar que el plugin aRSS por defecto no funciona, aparece una línea vertical blanca en la barra...

Para que funcione necesitas tener instalado en tu equipo un paquete que por defecto no se incluye en la instalación de AWN.

Hacemos desde consola:

    sudo apt-get install python-feedparser

Una vez instalado ya puedes usar éste plugin.
Para añadir feeds edita el fichero:

    gedit .config/awn/applets/.feedlist

y añade la dirección de cada feed en una línea.


[SIZE="4"][B][U]You only have to edit the file below calling in the konsole:

gedit .config/awn/applets/.feedlist

here you should put the direction of the feed/rss (one feed direction per line) and automatically it will be refreshed , sorry for the bad english and !viva mexico!

if you want to follow the link here is it:

[http://www.lopst.com/index.php?paged=20](http://www.lopst.com/index.php?paged=20)[/U][/B][/SIZE]

About the kalendar, i have no idea.

---

