---
title: "Recuperar grub"
date: 2020-11-16
forum: Centroamerica Team
---

### Post by adeptus24 on 2020-11-16
Buenas,

Os comento, tenía una instalación con dual boot de ubuntu y windows 10 en discos separados, tuve que reinstalar windows y he perdido grub para el arranque, estoy haciendo la chapuza de arrancar con Super Grub2 Disk para detectar la particion de ubuntu y arrancarlo.

He intentado reinstalar grub2 arrancando ubuntu y reinstalandolo en el /dev/sda, no me da error, luego hago el update y todo ok, pero al arrancar no lo veo en la bios para ponerlo como opcion de arranque, hay alguna forma de recuperarlo? si no solo se me ocurre coger otro ssd igual (tengo varios) reinstalar ubuntu y hacer un dd de todo menos del /boot desde el disco que tengo para no perder todo el software y configuraciones que tengo ahora, pero no se si eso es optimo, os dejo como están particionados los dos discos:

nvme con windows 10:

NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
nvme0n1     259:0    0 953,9G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0   100M  0 part 
&#9500;&#9472;nvme0n1p2 259:2    0    16M  0 part 
&#9500;&#9472;nvme0n1p3 259:3    0 953,3G  0 part 
&#9492;&#9472;nvme0n1p4 259:4    0   510M  0 part 

SSD con Ubuntu 20.04.1 LTS

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111,8G  0 disk 
&#9500;&#9472;sda1   8:1    0  28,8G  0 part /
&#9492;&#9472;sda2   8:2    0    83G  0 part /home

PD: La instalación de ambos OS es en modo UEFI.

Saludos.
Santi.

---

### Post by CelticWarrior on 2020-11-16
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by adeptus24 on 2020-11-16
Buenas @CelticWarrior, he usado el boot-repair pero no ha funcionado, he tenido que hacerlo desde un usb bootable porque lanzandolo desde el sistema al ser instalacion EFI me daba un mensaje de aviso indicando que lo hiciese así, pero solo encuentra el arranque de windows, pero no el de ubuntu,

Saludos.

---

