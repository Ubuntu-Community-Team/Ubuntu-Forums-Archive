---
title: "Montar una red diskless"
date: 2010-05-04
forum: Centroamerica Team
---

### Post by jujoboro on 2010-05-04
Hola a todos,:popcorn:

Les comento a todos que me encuentro tratando de montar una red diskless, que no es una ltsp ya que en esta última todo es ejecutado en el servidor (desde el sistema operativo).  La diskless permite que el sistema operativo sea ejecutado en la estación por medio de recursos propios y otros aplicativos en el servidor.

Pues bien, después de muchas pruebas, y muchas recetas en la web, he logrado llegar al punto en el cual la terminal

Levanta el PXE   
Tiene dirección IP
Monta el archivo default del tftp
 ha logrado ver el kernel y da el mensaje: "Loading vmlinuz-xxxxxxxx"   donde xxxx es la versión en uso.=D>

El problema es que al momento de iniciar la carga file system me da el mensaje "Could not find ramdisk image: initrd.img xxxxxx"  donde xxxx es la versión en uso.](*,)


¿Alguien tiene alguna idea del problema o por donde empezar a desenredarlo?:confused:

Gracias de antemano:lolflag:

jujoboro

---

