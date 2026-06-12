---
title: "[SOLVED] ajuda amb particions"
date: 2008-02-24
forum: Catalan Team
---

### Post by lluisanunez on 2008-02-24
A veure, finalment me n'he sortit amb l'alternate i hem insta&#320;lat Ubuntu en un segon disc.
Enganxo el contingut del fstab. El problema és que la partició /data que hem fet no té permisos i que no la visualitza a l'escriptori ni a "llocs" com a volum muntat

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=45540a6d-beb4-44a1-a480-46938cf85282 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb4
UUID=62d46cda-73f8-4236-852a-4d7c8f73c9ed /data           ext3    defaults        0       2
# /dev/sdb2
UUID=d3ecde70-35b7-4b2d-bfd5-339aa500809c /home           ext3    defaults        0       2
# /dev/sda1
UUID=7C6C72136C71C902 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=1cfa5ccb-9800-4ec2-b99b-8c8fc766dee0 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by papapep on 2008-02-24
I on heu creat, i quins permisos té, el directori aquest /data on monteu la partició?

---

### Post by lluisanunez on 2008-02-24
Segons el fstab, això està a /dev/sdb2, no?

---

### Post by papapep on 2008-02-24
Però que sigui al fstab no implica que no s'hagi de crear el directori per a muntar-hi la partició. A quin punt de l'estructura del sistema de fitxers l'heu creat? M'explico?

---

### Post by lluisanunez on 2008-02-24
Això ho hem creat durant la insta&#320;lació amb l'alternate, és una partició primària anomenada /data, ara ja ho veig que no ho hem fet bé.
Al sistema de fitxers està directament a sota de /

---

### Post by papapep on 2008-02-24
Prova a crear el directori sota (per exemple) /home. Hauria de funcionar (de fet hauria de funcionar com ho heu fet, però vaja...)

Això que dius aquí:
> El problema és que la partició /data que hem fet no té permisos i que no la visualitza a l'escriptori ni a "llocs" com a volum muntat

què vols dir amb que "no té permisos"? Si al terminal fas un cd a /data ho troba? No hi pots copiar un fitxer?

---

### Post by lluisanunez on 2008-02-24
Mira, els permisos que té la partició /data:

---

### Post by papapep on 2008-02-24
Fuig, fuig (aquestes coses gràfiques les carrega el diable :-D). Digue'm què et mostra un:

```
ls -la /data
```

---

### Post by lluisanunez on 2008-02-24
```
  gina@ubuntu:~$ ls -la /data
total 24
drwxr-xr-x  3 root root  4096 2008-02-24 14:46 .
drwxr-xr-x 22 root root  4096 2008-02-24 15:00 ..
drwx------  2 root root 16384 2008-02-24 14:46 lost+found
gina@ubuntu:~$ 

  
```

---

### Post by papapep on 2008-02-24
Doncs tenim que el propietari és root, el qual pot fer de tot, els usuaris del seu grup poden llegir i executar, igual que la resta del món mundial. La impresió de pantalla que has posat abans ja deia una cosa semblant (deia que no n'era el propietari l'usuari que ho visualitzaba i que per això no els podia modificar).

Ara que ja sabem on som (al menys jo fins ara no ho sabia), què és el que vols fer que no funciona??

---

### Post by lluisanunez on 2008-02-24
Vull donar drets a l'usuari Gina, però primer volia saber si la partició estava ben feta
També volia que es visualitzi a l'escriptori i a "llocs"

---

### Post by papapep on 2008-02-24
Si per "la partició està ben feta" vols dir si tot funcionarà degudament, jo canviaria el propietari del directori i provaria a ficar-hi fitxers, sense més. De sortida no hi ha res que sembli que hagi d'anar malament.

EDICIÓ: Una cosa que podries verificar, si no ho has fet ja, per acabar de veure si realment estàs muntant /data a /dev/sdb2 és copiar un fitxer, accedir-hi, desmuntar la unitat i veure que realment no hi tens accés. Tornar-la a muntar i verificar que hi pots tornar a accedir.
El que es vegi a l'escriptori només et cal un enllaç al directori fet a l'escriptori. El tema de llocs no en tinc ni idea.

---

### Post by lluisanunez on 2008-02-24
Gràcies, fetes les comprovacions i tot OK.  Ara em quedaria una cosa per solucionar: hem insta&#320;lat Ubuntu al segon disc de l'ordinador (sdb), però el Grub s'ha posat al sda (o això li hem dit al programa d'insta&#320;lació) que és on hi ha el Hasefroch.  Hem fet això perquè el Hasefroch havia deixat de funcionar (diu que No encuentra el sistema), creiem que potser el disc s'ha fet malbé.  Les meves preguntes són: 
* com ens podem assegurar de quin disc fa servir el Grub? 
* com podem traslladar el Grub al disc secundari per poder desmuntar el primari?

---

### Post by papapep on 2008-02-24
**grub-install** crec que et farà la feina que vols

---

### Post by lluisanunez on 2008-02-24
Moltes gràcies, ja m'he baixat un manual de grub-install, i ho faré el proper dia que hi vagi.
Per cert, ha estat una "success story" que en diuen els ianquis. L'ordinador d'aquesta amiga va fer "puf" l'altre dia: el Hasefroch li treu un missatge de "No se encuentra el sistema, bla bla, presione (R) para recuperar" (però res). La BIOS també donava un missatge d'error com si la placa no detectés els discos. Hem posat el CD alternate d'Ubuntu a veure si ens donava més informació del desastre, però per la meva sorpresa ha reconegut tots els discos, m'ha deixat fer les particions i s'ha insta&#320;lat. Fins i tot l'ATI radeon l'ha reconeguda. Al final hi havia allà un *coro* d'admiradors d'Ubuntu entre amics i veïns
:KS

---

### Post by papapep on 2008-02-24
Volem fotografies de l'espectacle i la claca!!! :-D

---

