---
title: "Grub Error 18"
date: 2008-12-09
forum: Ecuador Team
---

### Post by ebola182 on 2008-12-09
Hola soy nuevo en esto... instale ubuntu 8.10 en mi compu junto con windows y al momento de encender mi compu me sale Error 18 Grub alguien me ppuede ayudar con esto gracias..............

---

### Post by caljohnsmith on 2008-12-09
Saludos, bienvenidos a los foros. :) A 18 Grub error suele ocurrir cuando se tiene un BIOS que no puede tener acceso a nada en el disco duro pasado 8.4 GB o 137 GB. Por lo general, la mejor manera de solucionarlo es hacer un ~ 200 MB ext3 en la partición de inicio de tu disco duro y, a continuación, al instalar Ubuntu, establecer el punto de montaje de la partición como "/boot". Pero si tienen todo listo Windows instalado en el comienzo de la unidad, no el tamaño del comienzo de la partición de Windows para la partición de 200 MB, o usted no será capaz de arrancar Windows después de eso. Si puede, que ayudaría a abrir un terminal (Aplicaciones> Accesorios> Terminal) y después de la salida:
```
sudo fdisk -lu
```
Y podemos trabajar a partir de ahí si lo desea.

---

