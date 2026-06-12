---
title: "L'ordinador no arrenca, necessito ajuda"
date: 2008-11-23
forum: Catalan Team
---

### Post by Satboy on 2008-11-23
Hola,
 L'altre dia vaig instal.lar via repositoris una aplicació per esborrar arxius innecessaris i així mantenir net l'**Ubuntu 8.10** (això és el què deia).Desprès de la neteja se'm va penjar i després de penjar-se em van desaparèixer les icones de l'escriptori.Via Synaptic vaig intentar tornar a instal.lar l'arxiu Ubuntu-Desktop i els seus altres arxius que hi van associats.L'intent va ser infructuós, ho vaig provar vàries vegades i no hi va haver manera ja que em va dir que faltaven alguns arxius.
 Vaig decidir reinicira l'ordinador i ara no passa ni del Grub.He vist que la versió del Kernel de l'Ubuntu 8.10 m'ha desaparegut i no més apareixen vàries versions del 8.04, quan he intentat "bootejar" l'ordinador amb alguna d'aquestes versions sempre obtinc el mateix resultat: **Error 15 file not found**

 Ja se que podria reinstal.lar l'Ubuntu però és que tinc molt material que no m'agradaria perdre (fotos, pelis, contactes del ThunderBird, etc..)

 He provat amb:

 -**SuperGrub disk**
 -**Ubuntu Rescue remix 8.10**
 -**System Rescue CD**

 Amb cap d'aquestes aplicacions me n'he sortit (la veritat és que no en tinc gaires nocions)

 Em podeu ajudar?
 Si cal reinstal·laré l' Ubuntu per vull, com a mínim, recupera el material més valuós que hi tinc!!
 
 Gràcies i A10!

David

---

### Post by PatrickVogeli on 2008-11-23
jo nomes entro a fer de taliban ortografic: booteja?? mira que hi ha maneres de dir-ho en català...

---

### Post by papapep on 2008-11-23
Arrenca l'ordinador amb un livecd i recupera les dades importants.

Respecte el programa "per mantenir l'ubuntu net" o "eliminar arxius innecessaris", cal recordar que això no és windows...ho dic per si algú veu el teu comentari i pensa que això és recomanable o necessari: sota cap concepte.

Ah!, i sí, "booteja" va un pèl més enllà de l'habitual en català :-)

---

### Post by Satboy on 2008-11-24
> **papapep said:**
> Arrenca l'ordinador amb un livecd i recupera les dades importants.

Respecte el programa "per mantenir l'ubuntu net" o "eliminar arxius innecessaris", cal recordar que això no és windows...ho dic per si algú veu el teu comentari i pensa que això és recomanable o necessari: sota cap concepte.

Ah!, i sí, "booteja" va un pèl més enllà de l'habitual en català :-)

Bon dia!
 Gràcies Papapep per la resposta!
 Em podries dir com ho puc fer per recuperar les dades importants amb el live CD? Ho he provat vàries vegades però no trobo el "meu" disc dur.
 Estic d'acord que "bootejar" no sona gaire català, però oi que m'heu entès??

 A10 i gràcies!

David

---

### Post by papapep on 2008-11-24
Doncs has de mirar quina partició és el teu disc dur i muntar-lo. Fent un:

```
sudo fdisk -l
```

o amb el Gestor de particions de l'entorn gràfic (Gparted), veuràs les particions que tens. Has d'esbrinar quina és la que et cal muntar per accedir a les teves dades. 

Suposant que la teva partició fos /dev/sda1, per muntarlo cal:

 - Crear un directori on muntar-lo (suposem que crees MeuDisc dins /home/satboy):

```
mkdir MeuDisc
```

i muntes la partició (suposant que és un sistema de fitxers EXT3):

```
sudo mount -t ext3 /dev/sda1 /home/satboy/MeuDisc
```

ara si entres dins /home/satbo/MeuDisc hauries de trobar-hi les dades.

> Estic d'acord que "bootejar" no sona gaire català, però oi que m'heu entès??

Evidentment, però no es tracta d'això...

---

### Post by oriolsbd on 2008-11-24
El Live CD, per defecte, no et munta el teu disc dur. En principi, això va molt bé perquè pots fer molta feina de particionat directament. Si obres un Nautilus, veuràs cadascuna de les particions del teu disc dur a la barra lateral esquerra (amb el nom d'etiqueta de cada partició). Si hi fas clic a sobre, te'l muntarà de manera temporal, i podràs fer-te còpia de seguretat del que vulguis.

Salut!

---

### Post by Satboy on 2008-11-24
Bon dia de 9,
 Gràcies a tots, ja ho provaré quan sigui a casa i us en faré cinc cèntims del resultat.
 
 Gràcies de 9 i A10!

 P.D. Amb el Live Cd es poden gravar CD/DVD??

---

### Post by marteljorge on 2008-11-24
> **Satboy said:**
> Bon dia de 9,
 Gràcies a tots, ja ho provaré quan sigui a casa i us en faré cinc cèntims del resultat.
 
 Gràcies de 9 i A10!

 P.D. Amb el Live Cd es poden gravar CD/DVD??

clar que es pot, sempre que tinguis a més de l'unitat des de la que arrenquis  una gravadora de cd/dvd

---

### Post by Satboy on 2008-11-24
> **papapep said:**
> Doncs has de mirar quina partició és el teu disc dur i muntar-lo. Fent un:

```
sudo fdisk -l
```

o amb el Gestor de particions de l'entorn gràfic (Gparted), veuràs les particions que tens. Has d'esbrinar quina és la que et cal muntar per accedir a les teves dades. 

Suposant que la teva partició fos /dev/sda1, per muntarlo cal:

 - Crear un directori on muntar-lo (suposem que crees MeuDisc dins /home/satboy):

```
mkdir MeuDisc
```

i muntes la partició (suposant que és un sistema de fitxers EXT3):

```
sudo mount -t ext3 /dev/sda1 /home/satboy/MeuDisc
```

ara si entres dins /home/satbo/MeuDisc hauries de trobar-hi les dades.



Evidentment, però no es tracta d'això...

 Hola de 9!
 He seguit la primera instrucció i m'ha sortit això:

 Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a0530ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       24792   199141708+   f  W95 Ext'd (LBA)
/dev/sda5               1         131     1052194+  82  Linux swap / Solaris
/dev/sda6   *         132       24792   198089451   83  Linux

Quina és al meva partició?
I un cop que sàpiga quina és, com tinc de posar aquesta ordre?

sudo mount -t ? /dev/? /home/satboy/MeuDisc



 Gracies, de 9, i A10!

David

---

### Post by Satboy on 2008-11-24
Hola de 9,
 Aquesta tarda m'he comprat un disc dur extern per guardar-hi tots els arxius importants i ara no m'hi deixa entrar, que puc fer-hi?

 Moltes gràcies, i perdoneu-me si em faig molt pesat!

[IMG]http://img148.imageshack.us/img148/1339/discdurexternmi3.jpg[/IMG]

A10!

David

---

### Post by auska1714 on 2008-11-24
tel detecta el terminal (lsusb)?

---

### Post by papapep on 2008-11-24
Concepte: el "terminal" no detecta res, és una finestra als budells del sistema operatiu que serveix per veure, en aquest cas, quins dispositius detecta (ara sí) el nucli (kernel) del gnu/linux.

---

### Post by Satboy on 2008-11-25
> **papapep said:**
> Concepte: el "terminal" no detecta res, és una finestra als budells del sistema operatiu que serveix per veure, en aquest cas, quins dispositius detecta (ara sí) el nucli (kernel) del gnu/linux.

 Bon dia!
 Com, què dius Papapep?:confused: Em temo que em sona a xinès!:(
 Com ho tic de fer això?

 Gràcies i A10!

David

---

### Post by papapep on 2008-11-25
L'auska1714 t'ha dit que facis a un terminal:

```
lsusb
```

i el que jo he explicat, per no confondre quí fa què, és que la ordre "lsusb", executada a l'intèrpret d'ordres, llista els dispositius USB (com el teu disc dur, el ratolí, etc..)que el [nucli]("http://ca.wikipedia.org/wiki/Nucli_del_sistema_operatiu") del sistema operatiu detecta i, en condicions normals, gestiona correctament.

Com que, de fet, veient la icona de la imatge que has posat abans, ja sembla que t'aparegui el disc exter encara que no es munti, és clar que ja el detecta, o sigui que no cal que executis la ordre.

Potser és un problema de permisos. Fent botó de la dreta del ratolí damunt el disc i fent clic a  "Munta el volum", què fa? Ja ve formatat amb algun sistema de fitxers el disc extern? si fas aquella ordre d'abans:

```
sudo fdisk -l
```

es veu el nou disc i la/les seves particions?

---

### Post by Satboy on 2008-11-25
> **papapep said:**
> 
...
Fent botó de la dreta del ratolí damunt el disc i fent clic a  "Munta el volum", què fa?
...


Hola de 9,
 Doncs no fa res de res, com si sentis ploure...o potser tinc d'esperar una estona?

A10!

David

---

### Post by papapep on 2008-11-25
> o potser tinc d'esperar una estona?


Més de 2, 3 ó 4 segons, no sol ser l'habitual.

Si fas a un terminal (amb el disc dur extern connectat):

```
ls -la /media
```

què surt? enganxa'ns-ho, si us plau.

---

### Post by Satboy on 2008-11-25
> **papapep said:**
> Més de 2, 3 ó 4 segons, no sol ser l'habitual.

Si fas a un terminal (amb el disc dur extern connectat):

```
ls -la /media
```

què surt? enganxa'ns-ho, si us plau.

 Hola novament,
 El què m'ha sortit és això:

 ubuntu@ubuntu:~$ sudo ls -la /media
total 8
[B]drwxr-xr-x  3 root root  100 2008-11-25 19:25 .
drwxr-xr-x 23 root root  320 2008-11-25 19:16 ..
drwxr-xr-x 21 root root 4096 2008-11-20 23:52 disk
-rw-r--r--  1 root root   58 2008-11-25 19:25 .hal-mtab
-rw-------  1 root root    0 2008-11-25 19:21 .hal-mtab-lock[/B]

 A10!

David

---

### Post by papapep on 2008-11-25
Què et surt si fas?:

```
ls -la /media/disk/
```

---

### Post by Satboy on 2008-11-25
> **papapep said:**
> Què et surt si fas?:

```
ls -la /media/disk/
```

 Hola!

 Doncs em diu que no existeix:

 **ls: cannot access /media/disk/: No such file or directory**

A10!

David

---

### Post by papapep on 2008-11-25
Executa en un terminal la ordre "lsusb" que t'hem comentat abans, amb el disc connectat i sense estar-ho, i enganxa ambdós resultats.

---

### Post by Satboy on 2008-11-26
> **papapep said:**
> Executa en un terminal la ordre "lsusb" que t'hem comentat abans, amb el disc connectat i sense estar-ho, i enganxa ambdós resultats.

Bon dia!
 Ara sóc a la feina (7 a 14h) aquesta tarda ho faré i ja us en comentaré els resultats.

 A10!

David

---

### Post by Satboy on 2008-11-26
> **papapep said:**
> Executa en un terminal la ordre "lsusb" que t'hem comentat abans, amb el disc connectat i sense estar-ho, i enganxa ambdós resultats.

 Hola,
 Ja torno a estar connectat de 9,

 He fet la prova que tu m'has dit amb el disc **connectat**, i aquest n'és el resultat:

 ubuntu@ubuntu:~$ sudo lsusb
**Bus 005 Device 007: ID 04fc:0c25 Sunplus Technology Co., Ltd** 
Bus 005 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 002: ID 04cc:1122 Philips Semiconductors Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:1004 Hewlett-Packard DeskJet 970c/970cse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
 I aquest és el resultat amb el disc **desconnectat**:

 ubuntu@ubuntu:~$ sudo lsusb
Bus 005 Device 004: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 002: ID 04cc:1122 Philips Semiconductors Hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:1004 Hewlett-Packard DeskJet 970c/970cse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

  L'única diferència que hi veig és el primer "Bus" de dalt (en negreta) , que a sota no hi surt.

 A10!

David

---

### Post by auska1714 on 2008-11-26
No es que ho domini massa, però diria que si que tel detecta...

---

### Post by PatrickVogeli on 2008-11-26
el connectes directament al PC o través d'un lladre d'usb?

---

### Post by Satboy on 2008-11-26
Hola,
 Està connectat directament a la CPU.Si, sembla que el detecta però no m'hi deixa treballar, diu que no es pot muntar.
 
 A10!

 David

---

### Post by papapep on 2008-11-26
I fent:

> cat /etc/fstab

què surt?

---

### Post by Satboy on 2008-11-27
> **papapep said:**
> I fent:



què surt?

Bon dia!
Aquesta tarda ho provaré! :wink:

 A10!

David

---

### Post by Satboy on 2008-11-27
> **papapep said:**
> I fent:



què surt?

 Hola!
 Ja ho he provat i em surt això:

 ubuntu@ubuntu:~$ sudo cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

 A10!

David

---

### Post by Satboy on 2008-12-02
Bona tarda,
 Mirant per Internet, ha vist en una pàgina que tenia d'escriur la comanda:

 > "sudo fdisk -l"

 El resultat que m'ha donat és el següent (el què està en negreta és on crec que hi ha el problema)
 Algú sap com ho puc sol·lucionar?

>  Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3a0530ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       24792   199141708+   f  W95 Ext'd (LBA)
/dev/sda5               1         131     1052194+  82  Linux swap / Solaris
/dev/sda6   *         132       24792   198089451   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

**Disk /dev/sdb doesn't contain a valid partition table**

 Gràcies i A10!

David

---

