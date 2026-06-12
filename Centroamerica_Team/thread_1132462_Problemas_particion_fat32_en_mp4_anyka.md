---
title: "Problemas particion fat32 en mp4 anyka"
date: 2009-04-21
forum: Centroamerica Team
---

### Post by meldon12 on 2009-04-21
Que tal chicos, me acabo de comprar [esto en yoytec](http://www.yoytec.com/product_info.php/products_id/3927?osCsid=4ef0452be40f3d8f1ca8f4f2c61c5ea1) y cuando lo conecto al usb no monta la particion, aparecen los 2 iconos de las particiones en la carpeta de unbidades pero cuando les doy 2click no los monta, solo dice que no se puede montar, al intentar usar el gparted y formatearlo a fat32 aparece lo siguiente:

> El dispositivo /dev/sdb tiene un tamaño lógico de sector 4096. No todas las partes de GNU Parted soportan eso por ahora, y el código que lo hace es ALTAMENTE EXPERIMENTAL.


.... cuando estaba escribiendo esto intente por ultima vez despues q me salia el mensaje q cite arribe, luego lo reconecte y ahora si lo reconoce... en este caso como parece estar "solucionado" ... ¿abra alguien que pueda explicarme que rayos paso? de un momento a otro fuciono y antes no :S

saludos a todos

meldon12

---

### Post by eivar on 2009-04-24
Hola meldon este es un caso extraño... 
Supongo que el gparted cambió algo en tu tabla de particiones y esto permitió que el dispositivo sea detectado.
De cualquier forma ¿en que formato estaba originalmente? ¿gparted logró formatear o te mandó este error y falló el proceso?

Saludos.

---

### Post by meldon12 on 2009-04-25
El formato era fat32, asi vino de fábrica, pero solamente lo leía el windows normal. al principio me mandaba el error y no lo podia formtear pero en ese caso que pongo arriba me mando el error y lo formatio sin problemas...

saludos

PD: desde ubuntu 9.04... me encanta jeje

---

### Post by eivar on 2009-04-27
> **meldon12 said:**
> El formato era fat32, asi vino de fábrica, pero solamente lo leía el windows normal. al principio me mandaba el error y no lo podia formtear pero en ese caso que pongo arriba me mando el error y lo formatio sin problemas...

saludos

PD: desde ubuntu 9.04... me encanta jeje
:lolflag: bueno me alegra que ahora funcione bien.
Saludos. :P

---

