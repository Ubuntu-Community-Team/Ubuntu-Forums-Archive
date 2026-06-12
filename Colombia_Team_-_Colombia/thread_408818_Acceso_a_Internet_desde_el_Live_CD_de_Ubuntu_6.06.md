---
title: "Acceso a Internet desde el Live CD de Ubuntu 6.06"
date: 2007-04-13
forum: Colombia Team - Colombia
---

### Post by sirgazil on 2007-04-13
Hola todos,

Tengo un problema para conectarme a Internet con Ubuntu 6.06 (estoy usando el Live CD).
Seguí los pasos de la guía de Ubuntu para configurar una conexión a Internet ADSL usando un modem PPPoE. La primera vez todo salió bien, pude conectarme y navegar. Pero al día siguiente, seguí el mismo procedimiento y la conexión no funcionó. 

A continuación está el procedimiento que seguí para establecer la conexión y lo que me aparece al escribir plog en el Terminal:

ubuntu@ubuntu:~$ sudo pppoeconf
Plugin rp-pppoe.so loaded.
ubuntu@ubuntu:~$ plog
Apr 13 17:41:11 ubuntu pppd[6729]: Remote message: MSL
Apr 13 17:41:11 ubuntu pppd[6729]: PAP authentication succeeded
Apr 13 17:41:11 ubuntu pppd[6729]: peer from calling number 00:90:1A:A0:3E:A0 authorized
Apr 13 17:41:11 ubuntu pppd[6729]: replacing old default route to eth0 [192.168.0.102]
Apr 13 17:41:11 ubuntu pppd[6729]: Cannot determine ethernet address for proxy ARP
Apr 13 17:41:11 ubuntu pppd[6729]: local IP address 190.24.35.115
Apr 13 17:41:11 ubuntu pppd[6729]: remote IP address 10.32.1.32
Apr 13 17:41:11 ubuntu pppd[6729]: primary DNS address 200.75.51.132
Apr 13 17:41:11 ubuntu pppd[6729]: secondary DNS address 200.75.51.133

Ya he intentado conectarme varias veces y la conexión sigue sin funcionar.

Cuando estoy en Windows la conexión funciona perfectamente.

Estos son algunos datos de mi computador, por si acaso:

S.O.: Windows XP Pro Service Pack 2
Procesador: AMD Athlon XP 2200+ 1.82GHz
Memoria RAM: 512 MB
Modem: HSP56 MR (SIS)
Adaptador de red: SIS 900-Based PCI Fast Ethernet Adapter

Gracias de antemano

---

### Post by dcantomo on 2007-04-16
Por favor cuentame que procedimiento estas siguiendo.

Cordialmente,


DIEGO ALEJANDRO CANTOR MORALES

---

### Post by sirgazil on 2007-04-16
¿Diferente al que describí en mi publicación inicial? Solo puedo agregar que en el programa que se abre para configurar la conexión a Internet (**sudo pppoeconf**), respondo YES a todas las preguntas e ingreso mi nombre de usuario y clave proporcionadas por mi proveedor de servicios de Internet. También usé el comando **pon dsl-provider**, pero todo sigue igual.

---

### Post by dcantomo on 2007-04-16
Disculpame tienes toda la razon; mi pregunta es revisaste los DNS y la puesta de enlace en la configuracion de red?

---

### Post by sirgazil on 2007-04-16
Perdón, pero no sé qué es revisar los DNS ni la puesta de enlace :confused: 
Debo agregar que soy nuevo en Ubuntu, apenas lo estoy probando desde el Live CD.

---

### Post by sirgazil on 2007-04-17
Ya no tengo problemas para conectarme a Internet.

Lo que paso fue que estaba siguiendo [[COLOR="DarkOrange"]esta guia de conexion para Ubuntu[/COLOR]]("http://wiki.ubuntu.com/ADSLPPPoE/") al pie de la letra.

Lo unico que hice fue seleccionar NO en la segunda pantalla del programa que se abre al escribir **sudo pppoeconf** en el terminal, y listo. Esta publicacion la escribi usando el Live CD.

Gracias de todas formas.

Perdon por la falta de tildes, es que con esta configuracion de teclado no se como usarlas.:D

---

