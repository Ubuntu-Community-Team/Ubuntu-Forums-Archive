---
title: "Problemes instal·lant una EPSON STYLUS DX4400"
date: 2008-10-15
forum: Catalan Team
---

### Post by lo gambusí on 2008-10-15
Salut!

Ha arribat a les meues mans una impressora EPSON STYLUS DX4400. Estic seguint los passos [d'este]("http://blog.toranks.es/instalar-impresora-epson-stylus-dx4400-e") bloc per instal·lar-la, però ni l'escàner ni la impressora em funcionen. 

Respecte l'escàner, instal·lo els paquets (prèviament convertits a .deb) que em diu a la guia, i no hi ha problema. Però a l'hora de provar-lo poso en marxa l'xsane i se'm queda penjat quan intento fer alguna cosa. A més, la impressora no fa cap soroll, ni moviment, ni res.

Respecte la impressora directament no és detectada per l'ubuntu, tal i com podeu vore a [esta]("http://img159.imageshack.us/img159/5140/capturaeo6.png") imatge.

Alguna idea? Estic fent jo alguna cosa malament? Moltes gràcies :)

---

### Post by lo gambusí on 2008-10-17
Cap proposta? :)

---

### Post by enricXIII on 2008-10-17
Home, segur que es pot fer alguna cosa...que jo desconec.
Només comentar que jo vaig retornar 2 Epson a la botiga davant la gran dificultat que tenia per instalarles, que encara que segurament es pot, em semblava una burrada innecessaria que fos tant complicat tenint altres marques a l'avast que podia instal.lar sense tant d'enrenou...
Estaré atent a aquest fil per si resulta que es mes fàcil del que jo vaig trobar en el seu moment...Sort!

---

### Post by lo gambusí on 2008-10-19
gràcies

---

### Post by ealbert on 2008-10-21
A aquestes alçades és possible que aquest problema ja l'hagis solucionat, per si no fos així t'adjunto unes adreces on parlen de Epson i en el lloc de descàrregues figura concretament la DX 4400

Ubuntu- Instalación de una impresora multifunción EPSON DX8450:
[http://www.etanonline.fr/es/2008/ubuntu-installer-une-imprimante-multifonction-espson-dx8450/](http://www.etanonline.fr/es/2008/ubuntu-installer-une-imprimante-multifonction-espson-dx8450/)

Descàrregues en el apartat "Form for download":
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

Sort!

---

### Post by lo gambusí on 2008-10-21
Gràcies, company.

Per desgràcia encara no ho he solucionat. De fet crec que ho tinc fotut, perquè ni tan sols me la reconeix:

> logambusi@logambusi-laptop:~$ lsusb
Bus 005 Device 002: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 062a:0000 Creative Labs Optical mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


---

### Post by papapep on 2008-10-21
I executant aixo 

```
dmesg | tail -20
```

després de connectar-la al port USB (un cop engegada, clar), què et mostra?

---

### Post by lo gambusí on 2008-10-21
> logambusi@logambusi-laptop:~$ dmesg | tail -20
[  134.704621] type=1503 audit(1224617482.064:12): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6302 profile="/usr/sbin/cupsd"
[  134.704635] type=1503 audit(1224617482.064:13): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6302 profile="/usr/sbin/cupsd"
[  134.704647] type=1503 audit(1224617482.064:14): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6302 profile="/usr/sbin/cupsd"
[  199.277081] CE: hpet increasing min_delta_ns to 15000 nsec
[ 2346.949066] CE: hpet increasing min_delta_ns to 22500 nsec
[ 2511.203822] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
[ 3325.745173] CPU0 attaching NULL sched-domain.
[ 3325.745193] CPU1 attaching NULL sched-domain.
[ 3325.752324] CPU0 attaching sched-domain:
[ 3325.752336]  domain 0: span 0-1 level MC
[ 3325.752342]   groups: 0 1
[ 3325.752351]   domain 1: span 0-1 level CPU
[ 3325.752356]    groups: 0-1
[ 3325.752367] CPU1 attaching sched-domain:
[ 3325.752372]  domain 0: span 0-1 level MC
[ 3325.752376]   groups: 1 0
[ 3325.752384]   domain 1: span 0-1 level CPU
[ 3325.752388]    groups: 0-1
[ 3347.692165] usb 4-1: reset low speed USB device using uhci_hcd and address 3
[ 3352.164139] usb 4-1: reset low speed USB device using uhci_hcd and address 3
logambusi@logambusi-laptop:~$ 


Per a què serveix, això que m'has dit?:)

---

### Post by papapep on 2008-10-21
Doncs per a veure les últimes 20 línies ([tail]("http://www.monkey.org/cgi-bin/man2html?tail") -20) del [dmesg]("http://www.monkey.org/cgi-bin/man2html?dmesg").

I fer el lsusb sense la impressora, què et mostra?
Ho has provat a diferents ports usb?

---

### Post by lo gambusí on 2008-10-21
Exactament lo mateix::?

> logambusi@logambusi-laptop:~$ lsusb
Bus 005 Device 002: ID 046d:0896 Logitech, Inc. OrbiCam
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 062a:0000 Creative Labs Optical mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Sí que ho he provat amb diferents ports i em diu el mateix...

---

### Post by papapep on 2008-10-21
I l'impressora a un altre ordinador (amb el SO que sigui), funciona? és el mateix procés de verificació de sempre.....

---

### Post by lo gambusí on 2008-10-21
L'he provat amb un altre 8.10 i amb un LiveCD Alpha6 del 8.10 i no me'l reconeix a cap.

---

### Post by papapep on 2008-10-22
Si el que vols dir és que ho has provat a altres ordinadors, aleshores la que està morta és la impressora...

---

### Post by lo gambusí on 2008-10-22
Sí, era amb altres ordinadors.

---

### Post by sakuraya on 2008-10-24
Molt bones. El meu cas ha estat una Epson Stylus SX205. També semblava que estava tot bé, però la impresora no feia res. He estat durant uns dies marejant la perdiu fins que per fí he pogut imprimir, i tot bé. No tinc gaires coneixements perquè fa poquet que estic utilitzant ubuntu, però he seguit al peu de la ratlla els següents passos: (sempre tenint en compte que no és la mateixa impresora exactament).
1) a [http://www.epson.es/support/](http://www.epson.es/support/) selecciones la teva impressora i el sistema operatiu. Això et descarrega un arxiu html. Entres i sel.lecciones multifunció.
2) aniràs a parar a la pàgina de "avasys". Ahí pots descarregar-te tots els arxius que necessites. Veuràs que al sistema "CUPS" hi ha un help. Seguint exactament aquests passos, a mí m'ha funcionat a la perfecció.

No sé si t'hauré ajudat una mica, perquè tal com t'he dit no hi entenc gaire. Ja diràs com t'ha anat i si et puc ajudar més.

Bona sort!):P

---

