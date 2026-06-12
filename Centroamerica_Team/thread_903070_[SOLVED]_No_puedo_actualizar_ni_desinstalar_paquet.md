---
title: "[SOLVED] No puedo actualizar ni desinstalar paquetes"
date: 2008-08-27
forum: Centroamerica Team
---

### Post by Rasta456 on 2008-08-27
Esto ya me ha pasado 2 veces y ha sido la causa e que gane experiencia insalando ubuntu.
Lo que pasa es que un dia bajando un programa de los repositorios creo que era wine tube que apagar la pc de forma ordinaria porque se congelo y cuando volvi a iniciar decidi instalar win nuevamete y qxopaloco sale disq
E: dpkg was interrupted, ou most manually tun dpkg --configure-a
bueno y lo otro que salia ay la vaina loco esq voy a la erminal y escribo sudo dpkg--configure -a y me sale to disq 
dpkg: error de tratamiento, en el fichero /var/lib/dpkg/updates/0000 cerca de la linea 1 y abajo me sale que el nombre del campo TDB dbe estar seguido por dos punto.
Por favor ayudenme he buscado en todos lados y no encuenro solucion.

---

### Post by mocoloco on 2008-08-28
Puedes intentar con el modo de recuperacion.  Al arrancar tu maquina, se presenta el menu de GRUB (de repente tienes que apretar ESC para verlo), y tienes la opcion que en ingles se llama "Recovery mode", no se si sera traducido pero debe parecerse.
Despues del texto te dara un menu, y una opcion es algo que ver con arreglar paquetes (Fix broken packages, algo asi).  Ve si eso te lo arregla.

---

### Post by Rasta456 on 2008-08-28
como asi es donde salen los sistemas operativos 
disq escoga el s.o de su preferencia
seleccionas ubuntu
y el menu que se carga
hay
donde salen los kernel 
y el otro sistema operativo

---

### Post by eivar on 2008-08-28
Hola, me parece haber leído por algún lado que es un archivo en la carpeta /var/ que hay que eliminar, no recuerdo los detalles pero recuerdo que lo leí en el foro de [www.ubuntu-es.org](www.ubuntu-es.org).

Suerte.

---

### Post by Rasta456 on 2008-08-28
Hice lo que me dijiste Mocoloco entre en el recovery mode y me aparecio reapir broken packages le di pero me salio lo mismo you most manually run dpkg --configure -a y ya sabes el resto creo que no me funciono pero gracias de todos modos.

---

### Post by Rasta456 on 2008-08-28
a

---

### Post by Rasta456 on 2008-08-28
Gracias por decime lo del directorio /var/ 
cuando lei despues de ejecutar el comando sudo dpkg --configure -a
me aparecia la direccion /var/lib/dpkg/updates/0000
ese archivo 0000
habia que eliminarlo pero me costo unos minutos pues desde interfaz no lo pude eliminar tubo que ser desde la terminal pero mejoer que lo hico yo solo pues esto me ha pasado varias vases y como dice n lo que no te dana el sistema te da experiencia gracias y Bless para todos.:):popcorn::lolflag:

---

