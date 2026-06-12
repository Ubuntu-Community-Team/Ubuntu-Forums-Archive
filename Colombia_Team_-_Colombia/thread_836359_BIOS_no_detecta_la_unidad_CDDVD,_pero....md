---
title: "BIOS no detecta la unidad CD/DVD, pero..."
date: 2008-06-21
forum: Colombia Team - Colombia
---

### Post by Fhernd on 2008-06-21
¡Hola a Todos!


El problema que voy a redactar a continuación se me presentó ayer durante la tarde mientras que usaba mi equipo sin hacer modificaciones críticas al sistema, es decir, tan solo navegando la Web.

**Problema**:

El problema consiste en que la unidad de CD/DVD no es reconocida por el BIOS pero ésta si se muestra en el listado de dispositivos de arranque, e **incluso** es posible hacer boot y cargar un LiveCD.

Ahora pasando a los SOs, esta unidad no es detectada por ninguno de los dos. En Windows no aparece en el Administrador de dispositivos, y en Ubuntu no aparece el archivo especial en el directorio /dev/


A continuación adjunto unos imágenes para que quede más claro:

[[IMG]http://img118.imageshack.us/img118/4304/biosmainzf6.th.jpg[/IMG]](http://img118.imageshack.us/my.php?image=biosmainzf6.jpg) [[IMG]http://img45.imageshack.us/img45/5751/biosbootkx4.th.jpg[/IMG]](http://img45.imageshack.us/my.php?image=biosbootkx4.jpg) [[IMG]http://img292.imageshack.us/img292/2170/bootmenupj6.th.jpg[/IMG]](http://img292.imageshack.us/my.php?image=bootmenupj6.jpg)

Actualmente tengo instalado dos sistemas operativos: Windows XP SP2 y Ubuntu 8.04 ambos en la partición de disco duro y que hasta el momento no han generado conflicto alguno por su uso.


**Descripción del equipo**:

**Marca/Modelo**: TOSHIBA Satellite A205-S4639
**H.D.D.**: 160GB + 120GB
**RAM**: 3GB DDR2
**Vídeo**: NVIDIA GeForce Go 7300
**Unidad Óptica**: *PIONEER DVD-RW DVR-K17LF*

Agradezco inmensamente cualquier respuesta a este post que ayude a solucionar este problema.

PD: Ya intenté actualizando el BIOS, y tampoco dio resultado.


¡Hasta pronto!

---

### Post by lord_of_me on 2009-02-19
es probable que el firmware del dispositivo no sea reconocido, en la mayoria de los casos es una incosistencia del mismo..

Tal vez si pruebas usando otro lector DVD o CD y mirando la version del firmware.

---

### Post by Rohen on 2009-02-20
Algunas veces las instalaciones de algunos programas como Nero o Daemon Tools (para Windows) dañan el registry. No se si Ubuntu tambien tiene registry como Windows pero si por acaso has instalado algun programa como Nero, Daemon, o algun otro que utilize Virtual Devices (para Montar ISOs) podrias:

1. Desinstalar esos Programas
2. Desinstalar los drivers para el CD/DVD
3. En caso de Windows borrar el registry key asociado con el CD/DVD
4. Reiniciar
5. Reinstalar

Puedes usar este post para borrar el registry key:

[http://support.microsoft.com/default.aspx/kb/314060](http://support.microsoft.com/default.aspx/kb/314060)

Saludos,

Roh

---

### Post by germandario on 2009-11-02
A mi me pasó lo mismo, así que tuve que usar la línea de comando para buscar el nombre apropiado para el dspositivo usando  wodim -scanbus    o      wodim --devices   lo cual arroja el tipo de dispositivo; en mi caso arrojó /dev/scd0 y por ejemplo en el software para quemar (estaba usando mybashbur) venía configurado como /dev/cdrom.

También edité el  archivo  /etc/fstab   usando el comando   sudo nano /etc/fstab  lo cual me permitió editar el fstab para predeterminar la unidad de cd y dvd que en este caso debería ser   /dev/scd0   y no     /dev/cdrom

---

