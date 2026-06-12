---
title: "AR5006EG+asus a7k (wireless usando driver d windows o con los madwifi)"
date: 2008-04-21
forum: Centroamerica Team
---

### Post by sokcire on 2008-04-21
Salu2!

Tengo una portatil (asus a7k) con esta targeta wireless

atheros AR5006EG

He instalé Ubuntu 7

Siguiendo los pasos de varios manuales n donde todos concuerdan q se debe usar ndiswrapper para q funcione algunas targetas wifi....logre hacer que la targeta fuera reconocida por la pc....sin embargo no tengo internet aunque exista un proveedor cercano...ademas despues de reiniciarla no puedo usar los puertos usb....alguien tiene alguna idea de como resolver esto? ya he usado los driver net5211.inf, netathwx.inf, otros 2 q no recuerdo y el que viene en el cd por defecto q a proposito es para vista!....y los unicos q mejor han trabajado son los de net5211.inf

tambien he intentado con la ultima version de madwifi y naaada.....quizas sea por mi poca experiencia..q se yo...

Si alguien tiene alguna experiencia jugando con esto le agradecería cualquier iluminación...nos vemos!:)

---

### Post by eivar on 2008-04-22
Hola, no se si ya probaste con este manual: [http://develovers.blogspot.com/2008/02/wifi-ubuntu-atheros-5006eg-en-aspire.html](http://develovers.blogspot.com/2008/02/wifi-ubuntu-atheros-5006eg-en-aspire.html)

Por cierto casi olvido preguntar que versión de ubuntu instalaste 7.04 o 7.10 para poder ayudarte mejor.

Hasta luego.

---

### Post by sokcire on 2008-04-22
sabia q iban a preguntar eso jejeje...es la 7.10...no lo puse por el apuro de xponer antes irme a tirar a la cama... y sip...si lo use... pues n teoria despues de seguir los pasos todo debe funcionar pero bueno...como les comenté pude hacer que se viera las redes...pero no logré tener el servicio...ademas de que los puertos usb no son reconocidos despues de instalar los driver...despues de quitar los controladores (5211) vuelven a funcionar... se me ocurrio comenzar de cero... ya desinstale todo y comence de cero paso por paso..pero sigo teniendo el mismo problema.

Aqui les dejo parte del syslog en donde me aparece algunos mensajitos:

"device not accepting address 8, error -110
new high speed usb device using ehci_hcd and address 9"

y si se preguntan que manuales use...he revisado las 5 primeras paginas al realizar consultas con palabras como: "atheros 5006eg, madwifi, ndiswrapper, asus a7k, driver, linux, ubuntu" 

tambien me he fijado que la targeta de red este encendida... por si lo preguntan...ademas la pc reconoce la targeta...

hasta luego!

---

### Post by sokcire on 2008-11-23
Después de algunos meses volví a intentar resolver esto! y finalmente logré hacerlo con ubuntu 8.10! al principio me costó porque tuve inconvenientes al instalar directamente la versión 8.10, además que aunque encontraba las redes no lograba reconocer la constraseña!... bueno en resumen lo que hice fue instalar el paquete "linux-backports-modules-intrepid-generic", deshabilitar "“Soporte para  Atheros 802.11 wireless LAN cards”"  y  habilitar "Soporte para  5xxx series of Atheros 802.11 wireless LAN cards"....hasta aquí aparecia la red pero no me reconocia el password... me imagino que lo que me resolvio fue ejecutar en terminal modprobe ath_pci porque después de eso funciono todo bien!... cabe destacar que la el wireless de vista que tengo en otra partición dejo de funcionar antes de ejecutar modprobe... y hasta el momento de escribir este mensaje desconosco si funciona en win...en todo caso lo que hice anteriormente fue deshabilitar el soporte para 5xxx... y habilitar el que tenía y luego ejecutar modprobe... nos vemos y espero que esto le sirva a alguien +!


* referencia:
[http://b2dbuntu.wordpress.com/2008/11/11/atheros-wireless-en-ubuntu-810-intrepid-ibex/](http://b2dbuntu.wordpress.com/2008/11/11/atheros-wireless-en-ubuntu-810-intrepid-ibex/)

---

