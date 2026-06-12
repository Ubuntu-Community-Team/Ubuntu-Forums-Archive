---
title: "Buenas tardes, problema con archivos"
date: 2012-07-26
forum: Colombia Team - Colombia
---

### Post by netico14 on 2012-07-26
Buenas tardes, coloco otro problema para ver si me podrian colaborar, tengo en una empresa montado un servidor de archivos, donde almacene toda la informacion y bajo samba comparto los archivos con computadores windows, el problema es k monte ubuntu server 12.04 y he visto k desaparecen los archivos de uno de los discos montados, por ejemplo, los archivos de excel se transforman en .tmp, un ejemplo mas claro, hay una archivo de excel llamado "nomina2012" de un momento a otro desaparecio y en la ubicacion de este se encontraba uno de nombre "A44J88D.tmp" k antes no estaba, eso ha pasado ya con 3 archivos de excel super importantes para la empresa y k solo se encuentran en el servidor de ubuntu y en un disco externo que es el que se comparte, por favor si alguien me pudiera colaborar, no se que es ni que hacer, muchas gracias de antemano

---

### Post by albandy on 2012-07-27
Los archivos tmp te los genera el propio cliente windows. 
Respecto a lo de los ficheros que desaparecen, sería muy raro que fuera cosa  de samba o de ubuntu, lo más usual es que algún usuario los haya borrado o los haya movido (supongamos que accidentalmente). 

Te recomiendo que actives el sistema de auditoría de samba.
En este blog lo explican muy bien: [http://chicheblog.wordpress.com/2011/01/21/como-auditar-la-actividad-de-los-usuarios-en-samba/](http://chicheblog.wordpress.com/2011/01/21/como-auditar-la-actividad-de-los-usuarios-en-samba/)

---

### Post by netico14 on 2012-07-27
> **albandy said:**
> Los archivos tmp te los genera el propio cliente windows. 
Respecto a lo de los ficheros que desaparecen, sería muy raro que fuera cosa  de samba o de ubuntu, lo más usual es que algún usuario los haya borrado o los haya movido (supongamos que accidentalmente). 

Te recomiendo que actives el sistema de auditoría de samba.
En este blog lo explican muy bien: [http://chicheblog.wordpress.com/2011/01/21/como-auditar-la-actividad-de-los-usuarios-en-samba/](http://chicheblog.wordpress.com/2011/01/21/como-auditar-la-actividad-de-los-usuarios-en-samba/)

Albandy, muchas gracias por tu respuesta, activare la auditoria, lo extraño es k en la misma ubicacion donde estaba el archivo ejemplo "nomina2012.xlsx" aparece "A88d66f.tmp" como si ese temporal fuela el documento de excel original, mas no se puede acceder, ya ha pasado con otros 3 archivos de excel de uso frecuente

---

