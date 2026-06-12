---
title: "Problemas instalacion ubuntu 5.10"
date: 2007-01-30
forum: Colombia Team - Colombia
---

### Post by ABI90 on 2007-01-30
Estimada comunidad:
Soy nuevo en el mundo de linux. Me regalaron un IBM Netfinity 5000, lo tengo con un monitor IBM E74. Knoppix funciona. Pero quiero instalar Ubuntu 5.10, tanto el live-CD como el install CD fallan en el mismo lugar.
Sintomas:
- el monitor en el proceso de arranque (boot) se apaga de repente y queda en Stand by.
- justo antes de que esto pase Error: temporaly failure in name resolution [fail].

No es el CD porque funciona en otro computador. Mis sospechas son del monitor.

¿Que puedo hacer?

---

### Post by JunySan on 2007-01-31
Trata con Ubuntu 6.10.Yo tube un problema parecido en una IBM Thinkpad con Ubuntu 6.06 y cuando use 6.10 todo funciono.Suerte..!:D

---

### Post by beuno on 2007-01-31
> **ABI90 said:**
> Estimada comunidad:
Soy nuevo en el mundo de linux. Me regalaron un IBM Netfinity 5000, lo tengo con un monitor IBM E74. Knoppix funciona. Pero quiero instalar Ubuntu 5.10, tanto el live-CD como el install CD fallan en el mismo lugar.
Sintomas:
- el monitor en el proceso de arranque (boot) se apaga de repente y queda en Stand by.
- justo antes de que esto pase Error: temporaly failure in name resolution [fail].

No es el CD porque funciona en otro computador. Mis sospechas son del monitor.

¿Que puedo hacer?

Es probable que no sea el monitor, sino algun parametro adicional que tengas que agregar en la instalacion por algun problema de compatibildad con tu placa de video.

Lo de "Error: temporaly failure in name resolution [fail]" no es el problema, eso es porque no debe estar conectado a la red, o la configurada con DHCP.

Ante todo confirmanos con que version estes intentando instalar (5.10 creo que no existe).

---

### Post by ABI90 on 2007-02-01
Gracias por las respuestas... Pero

1) estoy usando version 5.10 (claro  que existe, tengo el CD original)

2) Por recomendaciones del foro, baje la ultima version 6.10 desktop. Peor aún... Muestra lo siguiente:

[105.298199] PnPBIOS: Unknown tag ´0x0´, length ´0´.
[105.298255] PnPBIOS: Unknown tag ´0x0´, length ´0´.
.
.
.
[106.541791] PnPBIOS: Resource structure does not contain an end tag.
[106.541718] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)
[106.541778]  _  

Y ahora si que quedo frito.

---

### Post by beuno on 2007-02-07
Te diria que pruebes instalar con la version "alternate" que es un instalador un poco menos bonito, pero mucho mas *compatible*.

---

### Post by cocotu on 2007-02-09
AB deberias indicar las especificaciones de tu maquina! Asi nosotros tenemos una idea mas precisa enves de ir a google.com y buscar tu modelo de PC.  Si quieres puedes tratar Xubuntu. Es una version "light" de Ubuntu y me ha trabajado con la mayoria de las PCs un poco mas viejas que yo he tratado.  Suerte!

---

### Post by ABI90 on 2007-02-10
Estaba un poco perdido... El computador que tengo es un servidor IBM Netfinity 5000, es un cascaron viejo. Pero a caballo regalao no se le mira el diente, aquí estan las especificaciones que me pidieron. No he probado el XUbuntu, pero tiene sentido, es algo de la tarjeta de video, que yo no se la veo por ningun lado. Seguire primero intentando con otras DISTROS. Gracias por su tiempo, seguiré informando de como va todo. 

IBM Netfinity 5000 61Y - Tower - 2-way - 1 x PIII 600 MHz - RAM (128X3=384 MB) - HD: (tiene 3 SCSI REMOVIBLES) - CD - Monitor : none 


Main Specifications
Product Description IBM Netfinity 5000 61Y - PIII 600 MHz   
Type Server   
Form Factor Tower   
Dimensions (WxDxH) 8.6 in x 23.8 in x 17 in   
Weight 63.9 lbs   
Localization English / United States   
Server Scalability 2-way   
Processor 1 x Intel Pentium III 600 MHz   
Cache Memory 512 KB (installed) / 1 MB (max) - L2 cache - Pipeline Burst   
RAM 128 MB (installed) / 2 GB (max) - SDRAM - ECC   
Storage Controller SCSI ( Ultra Wide SCSI ) - PCI ; IDE ( IDE ) - PCI   
Floppy Drive 3.5" 1.44 MB floppy   
Hard Drive None.   
Optical Storage CD-ROM   
Monitor None.   
Graphics Controller PCI - S3 Trio64V2/GX - 1 MB   
Networking Network adapter - PCI - Ethernet, Fast Ethernet   
Power AC 110/220 V ± 10% ( 50/60 Hz )

---

### Post by compa on 2008-12-31
Que tal!!
leo que tiene bastante que no actualizan este hilo, pero pues me encuentro en el mismo problema... al instalar ubuntu me sale el mismo problema, y de ahi no paso....
mucho les voy a agradecer si alguien logro instalar ubuntu o debian en esta maquina, IBM netfinity 5000, desinstale la raid y conecte el arreglo de los discos al puerto scssi de la tarjeta madre, y la tarjeta raid esta sin conexion, con ello logre instalar windos para brincar a linux... alguien tiene alguna idea? no quiero instalar con el wibi por aquello del NTFS.. ojala que alguien tenga alguna respuesta.... gracias!!!

---

### Post by magicfab on 2008-12-31
Compa por favor abra un nuevo hilo.

---

