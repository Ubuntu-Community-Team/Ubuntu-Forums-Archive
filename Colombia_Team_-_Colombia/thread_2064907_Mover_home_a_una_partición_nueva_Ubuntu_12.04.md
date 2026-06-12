---
title: "Mover /home a una partición nueva Ubuntu 12.04"
date: 2012-09-30
forum: Colombia Team - Colombia
---

### Post by gonedcc on 2012-09-30
Hola a todos, tengo dudas sobre mover /home a una partición nueva. El problemas es que el netbook que compre venía con ubuntu 12.04 ya montado, la primera ves que lo encendí empezó a instalarlo automáticamente y nunca me pregunto lo de las particiones, dejando el /home en / quiero dejar los archivos personales en una partición nueva para que no se pierdan en caso de reinstalar el OS. Ya hice la partición quedando así:

dev/sda1  fat32   hidden
/dev/sda2  ext4    boot     40.04 Gib
/dev/sda3  linux-swap
/dev/sda4  Extended         254.36 Gib
/dev/sda5  ext4             254.35 Gib    Personal

quiero mover /home de sda2 a sda5, creo que la partición sda5 no se está montando automáticamente y no se como comprobar si está bien creada la partición (permisos, tipo de archivo, etc..).

---

### Post by cc mauz on 2012-10-14
Formate la particion /dev/sda5 con ext4, luego copie todo lo que hay en /dev/sda2 ahí.
Luego modifica el /etc/fstab cambiendo la sda2 por sda5.

---

### Post by gonedcc on 2012-11-01
que pena la demora en la respuesta, me sirvió muy bien gracias!

---

