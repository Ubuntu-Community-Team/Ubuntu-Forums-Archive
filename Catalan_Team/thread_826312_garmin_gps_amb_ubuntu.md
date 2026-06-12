---
title: "garmin gps amb ubuntu"
date: 2008-06-11
forum: Catalan Team
---

### Post by kilian_cuerda on 2008-06-11
Bona nit, companys. Últimament estic tenint un problema amb cóm connectar, per a descarregar dades, una unitat gps (garmin vista hcx) al portàtil amb ubuntu. Ací m'he instal·lat també el software per a gps que ve a synaptic, el gpsbabel i el qlandkarte. En un principi pareixia no reconèixer la unitat. 

El cas és que, mirant i preguntant per ahí i en la xarxa, he trobat gent amb problemes similars al meu i bé, seguint les instruccions, el resultat al terminal ha sigut aquest:   

toshiba@toshiba-ubuntu:~$ gpsbabel -i garmin -f usb: -o gpx -F kilian.gpx
usb_set_configuration failed, probably because kernel driver ''
 is blocking our access to the USB device.
For more information see [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html)
toshiba@toshiba-ubuntu:~$ sudo modprobe usbserial
[sudo] password for toshiba: 
toshiba@toshiba-ubuntu:~$ lsusb
Bus 006 Device 003: ID 091e:0003 Garmin International GPSmap (various models)
Bus 006 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 007 Device 004: ID 059b:0274 Iomega Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
toshiba@toshiba-ubuntu:~$ gpsbabel -i garmin -f usb: -o gpx -F kilian.gpx
usb_set_configuration failed, probably because kernel driver ''
 is blocking our access to the USB device.
For more information see [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html)
toshiba@toshiba-ubuntu:~$ 

Pel que pareix la unitat gps connectada al port usb sí que és reconeguda, però té l'accés bloquejat. Accedint a l'adreça que s'inica, [www.gpsbabel.org/os/Linux_Hotplug.html](www.gpsbabel.org/os/Linux_Hotplug.html) , venen instruccions per a eixe problema, però no m'acabe d'aclarar, i no diu res per a la distribució ubuntu hardy heron 8.04, que és la que tinc. 

Per altre costat, al qlandkarte, quan se li diu download all, diu: Failed to query loaded maps. Failed to configure USB: could not set config 1: Operation not permitted

Podrieu tirar-me una maneta per a resoldre això? moltes gràcies.

---

### Post by argggg on 2008-06-12
A mi el qlanskart em funciona (tinc un venture Cx) si l'inicio com a root.

*sudo qlanskart*

Així que es cosa de permisos, però no he tingut temps "d'investigar" a on falten els permisos.
El gpsbabel encara no l'he pogut probar, però es probable que també tingui problemes amb els permisos

Salut!

---

### Post by argggg on 2008-06-12
Coi de butiffarrons!!

sudo qlandkarte   

Ara si :)

---

### Post by PellRoja on 2008-06-12
jo també he provat de baixar el qlandkarte i no hi ha hagut manera de baixar els mapes

---

### Post by argggg on 2008-06-13
Mmm els mapes del gps a mi tampoc me'ls baixa, Peró si que li puc carregar manualment (Load Map)

---

### Post by PellRoja on 2008-06-13
> **argggg said:**
> Mmm els mapes del gps a mi tampoc me'ls baixa, Peró si que li puc carregar manualment (Load Map)

d' on treus els mapes? :)

---

### Post by argggg on 2008-06-15
L'altre dia vaig trobar aquesta pagina de mapes que encara no he carregat al qlandkarte:
[http://garminmapsearch.com/?l=ca](http://garminmapsearch.com/?l=ca)

En tot cas els que he probat son uns que es diuen topospain i topohispania (ara no se de quin dels dos son els mapes que porto) Aquests mapes son de distribució lliure (em sembla).

Aqui tens alguns mapes solts (la majoria però estan en arxius executables per  insertar-los al mapsource), i el topohispania
[http://www.foromtb.com/showthread.php?t=77931](http://www.foromtb.com/showthread.php?t=77931)

En qualsevol cas, tots els mapes que puguis instalar a un garmin amb format img t'haurien de funcionar.

---

### Post by PellRoja on 2008-06-15
gràcies, m' ho miraré a veure si aconsegueixo fer-lo funcionar :)

---

