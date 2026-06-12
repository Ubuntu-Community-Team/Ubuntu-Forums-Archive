---
title: "[SOLVED] Montar un Pen Drive"
date: 2008-02-18
forum: Catalan Team
---

### Post by almogabber on 2008-02-18
Hola!!
Després d'actualitzar per enèsima vegada, m'han aparegut alguns problemes,

El primer, i més lleu, és que no em reconeix el Pen Drive, tot i que amb Feitsy si que ho feia (amb win també segueix anant bé).
Quan el connecto m'apareix el següent missatge advertint que no es pot muntar:
```
mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, pr other error
In some cases useful info is found in syslog - try dsmesg | tail or so
```

El curiós és que apareix a 'computer:///'; i si faig botó dret -> muntar, tampoc rutlla.

He vist que si faig botó dret -> propietats -> pestanya 'Volume', es poden afegir els paràmetres que veig que falten:
-punt de muntatge
-sistema de fitxers
-opcions de muntatge

Em podríeu ajudar a completar aquestes dades, i així poder muntar el pen drive i que hi pugui accedir?? 

Gràcies!!!!

---

### Post by guillemsola on 2008-02-18
Et diu que facis un 

 dmesg | tail

fes-ho i adjunta el que et diu. Què pot ser dóna alguna pista.

---

### Post by almogabber on 2008-02-18
Perdo, ja ho havia fet però se me n'ha anat... :P 

```
almogaver@almogaver-linux:~$ dmesg | tail
[224664.247928] sda: Write Protect is off
[224664.247944] sda: Mode Sense: 03 00 00 00
[224664.247952] sda: assuming drive cache: write through
[224664.247967]  sda: sda1
[224664.254302] sd 2:0:0:0: Attached scsi removable disk sda
[224664.254456] sd 2:0:0:0: Attached scsi generic sg1 type 0
[224665.141384] FAT: Unrecognized mount option "usefree" or missing value
[224692.902119] FAT: Unrecognized mount option "usefree" or missing value
[224698.633782] FAT: Unrecognized mount option "usefree" or missing value
[225749.898258] FAT: Unrecognized mount option "usefree" or missing value

```

---

### Post by papapep on 2008-02-18
Amb el pendrive posat, fes:

```
lsusb
```

i després:

```
cat /etc/fstab
```

enganxa el resultat de tot plegat.

---

### Post by guillemsola on 2008-02-18
Sembla un problema del gnome-mount. Has provat a muntar la unitat pel teu compte? Ho dic pq possiblement aixì serviria.

De totes formes prova això

En una terminal executa el **gnome-conf**

Has de buscar a** /storage/default_options/vfat**

Allí hi trobaràs les opcions que fa servir el gnome per muntar un sistema vfat

Has de treure l'opció **usefree** que sembla que és la que et dona problemes.

Ja diràs.

---

### Post by almogabber on 2008-02-18
**papapep:**```
almogaver@almogaver-linux:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 058f:6387 Alcor Micro Corp. 
Bus 001 Device 002: ID 0471:0855 Philips 
Bus 001 Device 001: ID 0000:0000  
almogaver@almogaver-linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=6c493899-9a22-4133-a2e3-e76cd980c861 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=FE78AB0878AABEB1 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb2 -- converted during upgrade to edgy
UUID=8d527f32-32a6-44b8-b1f8-bbd030fa8f2b /media/hdb2 ext3 defaults 0 2
# /dev/hdb5 -- converted during upgrade to edgy
UUID=9AE8AAA8E8AA81DD /media/hdb5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=cf484ab1-bb20-4408-8ad1-20ba1eb5110f none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

**angrychai:**```
almogaver@almogaver-linux:~$ gnome-conf
bash: gnome-conf: command not found

```
sobre el que dius de muntar-lo manualment, et refereixes a les propietats?? és que ho deia al primer missatge, però com que no m'ho heu comentat.. Afegint les dades de [punt de muntatge, sistema de fitxers i opcions de muntatge] no l'acceptaria??

Gràcies per l'ajuda!! :)

---

### Post by guillemsola on 2008-02-18
Se m'ha anat la pinça, el paquet a executar és

gconf-editor

Prova amb aquest millor.

Salut!

---

### Post by almogabber on 2008-02-18
Bingo!!!!!!

Copio el que he fet, per si de cas serveix per més endavant:

- obro terminal: **$ gconf-editor**
- s'obre l'editor de la configuració
- busco  **/storage/default_options/vfat**
- botó dret sobre la 'clau' i l'edito per treure el camp **usefree**

Moltes gràcies!!!

vaig a plantejar el següent problema.. :P

---

