---
title: "[SOLVED] Webcam - no es reconocida!"
date: 2007-08-28
forum: Ecuador Team
---

### Post by xarroyo on 2007-08-28
Hola,
Yo tengo la siguiente webcam, esta informacion la obtuve mediante la konsole haciendo:

lsusb

Esta es la informacion que aparecio

ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam. 
Como puedo hacer para que funcion en ubuntu fiesty fawn

He leido de otros sitios que tengo que bajar el spca5xx-source.. Lo hice a traves del Synaptics Package Manager.. tambien he bajado el  gspca... finalmente baje el camorama para poder probar la webcam. pero cuando ejecuto el programa aparece el siguiente mensaje

could not connect to video device (/dev/video0)
Please check connection..

Si tengo mi webcam conectada.. Si voy al folder /dev noto que no existe el /video0...

Si escribo el siguiente comando en konsole

ls -la /dev/video0

aparece el siguiente mensaje
 crw-rw---- 1 root video 81, 0 2007-08-20 17:20 /dev/video0

He leido de otros sitios que debo agregar a mi usuario para poder asignar el permiso para poder hacer uso de la camara...

sudo adduser nickUser video

que debo haceR? porq aun no logro hacer funcionar mi webcam!!
gracias por la atencion

---

### Post by hubuntu on 2007-08-29
Hola!

Segun ví hablasbas inglés así que te mando un link:

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Ahi puedes instalar el driver de acuerdo a tu versión de kernel.

(Si hablas francés -  [http://www.commentcamarche.net/s/install-cam-linux-z-star-microelectronics-corp-zc0301-webcam](http://www.commentcamarche.net/s/install-cam-linux-z-star-microelectronics-corp-zc0301-webcam))

---------------------------------

Existe tb un link aqui en los forums, que se refiere a ubuntu especificamente (en una Sony Vaio, pero es la misma cámara):

[http://ubuntuforums.org/archive/index.php/t-289836.html](http://ubuntuforums.org/archive/index.php/t-289836.html)

espero esto se a de tu ayuda.

R

---

### Post by xarroyo on 2007-08-30
Diria yo que las instrucciones de como proceder para la instalacion son sencillas:
El aplico para Debian Etch, pero es lo mismo para ubuntu.. Mi camara ya funciona!! Espero que sea de utilidad para los demas..

La unica verificacion que deben hacer es cuando empiezan hacer la parte de la seccion compilar, deben ante poner sudo...

y en la que dice ./configure reemplazarla por sudo ./gspca_build

[http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/](http://mmejiav.wordpress.com/2007/06/07/modulo-gspca/)

---

### Post by xarroyo on 2007-09-06
Mi problema fue finalmente resuelto.. este es el link!! el sitio esta en ingles...
[http://ubuntuforums.org/showthread.php?t=530727](http://ubuntuforums.org/showthread.php?t=530727)

---

