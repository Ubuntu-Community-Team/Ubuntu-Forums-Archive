---
title: "S'ignora el fitxer /home/.dmrc"
date: 2008-10-22
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-10-22
Bones.
Acabo de instal·lar Ubuntu 8.04 i he copiat tot el directori "home" d'un altre pc el qual te el mateix nom d'usuari que el creat de nou.
Cada cop que inicio l'ordinador hem surt el següent missatge: "S'ignorarà el fitxer HOME/.dmrc Es recomenable que el directori HOME sigui propietat de l'usuari ..."

Es greu? o pot ser un problema més endavant?
De moment funciona tot be, però és una mica emprenyador veure aquest missatge cada cop que inicio el pc.

Gracies qui m'escolti, salut.

---

### Post by papapep on 2008-10-22
```
sudo chown elteuusuari:elteuusuari /home/.dmrc
```

i

```
sudo chmod 744 /home/.dmrc
```

---

### Post by Miquel Ubuntero on 2008-10-22
miquel@miquel-laptop:~$ sudo chown miquel:miquel /home/.dmrc
[sudo] password for miquel: 
chown: no s’ha pogut accedir a «/home/.dmrc»: No such file or directory
miquel@miquel-laptop:~$ 

:confused:

---

### Post by papapep on 2008-10-22
Doncs l'has de buscar per saber on el tens per modificar les ordres en consonància :-)

---

### Post by PatrickVogeli on 2008-10-22
el tens a /home/miquel/.dmrc

---

### Post by Miquel Ubuntero on 2008-10-23
Val, ja he trobat l'arxiu.
Aquest es el seu contingut:
[Desktop]
Session=default

Però no tinc gaire clar que hi he d'afegir???

Gracies.

---

### Post by PatrickVogeli on 2008-10-23
no hi has d'afegir res, has de fer el que t'ha dit el papapep

---

### Post by Miquel Ubuntero on 2008-10-23
Disculpeu la meva gran ignorància!!!
Però lo que va dir en papapep no hem va sortir.
Crec que m'ho tindreu que dir com a un nen de 4 anys!

---

### Post by PatrickVogeli on 2008-10-23
Em sembla que hi ha alguns que esteu molt mal acostumats i se us de donar tot fet. Trobo que de llegir 2 cops tot el que s'ha escrit i parar-se a pensar una mica ni havia prou. Però bé:

sudo chown elteuusuari:elteuusuari /home/.dmrc
sudo chmod 744 /home/.dmrc

**+**

Doncs l'has de buscar per saber on el tens per modificar les ordres en consonància 

**+**

/home/miquel/.dmrc

**=**

sudo chown miquel:miquel /home/miquel/.dmrc
sudo chmod 744 /home/miquel/.dmrc

---

### Post by Josep Maria on 2008-11-25
Jo tinc un problema identic.
Vaig copiar el directori Home a un disc dur extern sense problemes, per tenir-ne una còpia de seguretat.
Ara, a l'engegar m'apareix : signorara el fitxer $HOME/.dmrc

He seguit els consells d'aquest fil i he posat al terminal :
sudo chown josepmaria:josepmaria /home/josepmaria/.dmrc

i després:
sudo chmod 744 /home/josepmaria/.dmrc

Però no ho he arreglat, continua sortint el mateix missatge.
Dec fer un error de sintaxi?

---

### Post by papapep on 2008-11-25
Primer mirem que sigui on hauria de ser. Fes a un terminal:

```
sudo updatedb
```

això pot trigar una estoneta depenent de la mida dels teus discs.

Quan estigui:

```
sudo locate .dmrc
```

i enganxa aquí el que et surti.

---

### Post by Josep Maria on 2008-11-26
Hola Papapep:Gràcies
Després de fer el que m'has dit surt això :
/home/josepmaria/.dmrc

Em demano com es deuen haver canviat els privilegis de home, tan sols per copiar la carpeta a un altre disc.

---

### Post by papapep on 2008-11-26
Enganxa el que surti fent:

```
ls -la /home/josepmaria/.dmrc
```

Ah, i també:

```
cat /etc/fstab
```

i 

```
sudo fdisk -l
```

---

### Post by Josep Maria on 2008-11-27
Hola Papapep:
Perdona que no t'hagi respost abans, un dia horrible a la feina.

Primer :
josepmaria@josepmaria-desktop:~$ ls -la /home/josepmaria/.dmrc
-rwxr--r-- 1 josepmaria josepmaria 28 2008-11-25 13:27 /home/josepmaria/.dmrc
(des de la barra abans de home fins al final, tot surt de color verd)

Segon :
josepmaria@josepmaria-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=74d114a4-69d0-4fe1-bb33-c6144fd93984 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=67c85188-88cb-4e92-b1da-53147e51f634 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Tercer : josepmaria@josepmaria-desktop:~$ sudo fdisk -l
[sudo] password for josepmaria: 

Disc /dev/sda: 160.0 GB, 160041885696 octets
255 heads, 63 sectors/track, 19457 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x80be80be

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19457   135805477+   f  W95 Estesa (LBA)
/dev/sda5            2551       14259    94052511    7  HPFS/NTFS
/dev/sda6           18869       19457     4731111    7  HPFS/NTFS
/dev/sda7           14260       18673    35455423+  83  Linux
/dev/sda8           18674       18868     1566306   82  Intercanvi Linux / Solaris

Les entrades a la taula de particions no estan en l'ordre del disc
josepmaria@josepmaria-desktop:~$ 


Espero que això et servieixi.

i Gràcies.

Josep Maria

---

### Post by papapep on 2008-11-27
I fent:

```
ls -la /home/
```

què surt?

---

### Post by Josep Maria on 2008-11-27
Bon dia.
Docs surt això :
josepmaria@josepmaria-desktop:~$ ls -la /home/
total 12
drwxr-xr-x  3 root       root       4096 2008-11-04 12:37 .
drwxr-xr-x 20 root       root       4096 2008-11-12 07:03 ..
drwxrwxrwx 60 josepmaria josepmaria 4096 2008-11-27 08:59 josepmaria
josepmaria@josepmaria-desktop:~$

---

### Post by papapep on 2008-11-27
Tens tot el directori personal amb permisos globals (777)

> drwxrwxrwx 60 josepmaria josepmaria 4096 2008-11-27 08:59 josepmaria

 el qual vol dir que qualsevol usuari, fins i tot un d'indesitjat, pot fer i desfer a voluntat...ho has fet volent?

Si vols esmerçar-ho, hauries de fer:

```
sudo chmod 755 /home/josepmaria
```

i després, fes:

```
sudo chmod 644 ~/.dmrc
```

i reinicia, a veure què tal...

---

### Post by Josep Maria on 2008-11-27
Hola Papapep:
Ara funciona.
L'unica cosa que he fet és copiar el directori home a un disc extern.
Altres vegades que ho havia provat, em deia que no tenia permisos.
Aquest cop he fet una instal.lacio neta d'Intrepid, he copiat el home sense que em demani res, i després m'he trobat amb aquest problema.
T'ho explico per si a algú altre li podria passar.
I ara, com que jo no he obert aquest fil, qui l'hauria de tancar?

I moltes gràcies.

---

### Post by papapep on 2008-11-27
Molt bé, Josep Maria, m'alegro de que hagi funcionat.
Respecte el fil, deixem-lo obert. En tot cas en Miquel ja el tancarà si ho ha arreglat i li sembla adient ;-)

---

### Post by Miquel Ubuntero on 2008-11-27
Hola de nou.
Disculpeu si no he dit res abans. Jo també he estat molt liat a la feina.
A més, el problema que aquí explicava no era l'únic problema que tenia amb Xubuntu. Per la qual cosa vaig "tirar la tovallola" i hem quedo de nou amb Ubuntu que hem va més be.
Podeu tancar el fil si ho veieu adient.
Salutacions cordials a tots, i a veure si ens veiem dissabte a Amer.
Salut!

---

