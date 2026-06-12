---
title: "[SOLVED] Com fer una partició per a dades?"
date: 2008-11-25
forum: Catalan Team
---

### Post by jinglada on 2008-11-25
Tinc un innobo del pcbox, intel C2D, que me'l van lliurar amb l'ubuntu 8.10 de 64 bits perquè van dir que el de 32 no es va deixar instal·lar.

La informació del meu sistema és: Linux joan-laptop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux.

És correcte el de 64 bits per al meu ordinador? M'ha semblat veure que el de 64 bits és per a processadors AMD, si no ho he entés malament. En un altre lloc diu: "Choose this to take full advantage of computers based on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core 2)".

Vull fer una partició per a dades i sobretot per a copiar les dades del HD del mac que se'm va morir el mes passat, per anar recuperant tot el que pugui. He de formatejar de nou o puc fer-ho d'alguna altra manera? 

Gràcies a la bestreta,
Joan

---

### Post by papapep on 2008-11-25
Hola Joan,

> És correcte el de 64 bits per al meu ordinador?

Si no ho fos no l'haurien pogut instal·lar. Tot i que és el primer cop que sento que una versió de 32 bits no es deixa instal·lar en un ordinador de 64, pero vaja, això ja és un altre tema...
Els sistemes operatius de 64 bits són per ordinadors amb processadors de 64 bits, siguin de la marca que siguin (mentre siguin compatibles, clar).

> Vull fer una partició per a dades i sobretot per a copiar les dades del HD del mac ...

Sempre pots refer les particions que tinguis, una altra cosa és a quin punt estàs ara (o sigui, quines particions tens creades al disc) i a quin punt vols arribar.

Tens dues maneres:

 1.- A un terminal:

```
sudo fdisk -l
```

 2.- A l'entorn gràfic: vas a Sistema > Administració > Editor de particions.

De les dues maneres pots veure com tens ara el(s) disc(s) del teu ordinador. A partir d'aquí, de saber com ho tens, podràs decidir què vols fer. :-)

---

### Post by open-pitu on 2008-11-25
El millor seria que instal·lessis gparted (estil Partiton Magic) i que miris com tens les particions de manera amigable. Si no el tens instal·lat:
```
$ sudo apt-get install gparted 
```
```
$ sudo gparted
```

A partir d'aquí ho tens gràficament i és molt inutïtiu de fer funcionar. Tot i així si tens dubtes pregunta per aquí!

---

### Post by Satboy on 2008-11-25
Hola!
 Jo et recomano la versió **Live CD** del Gparted.L'has de gravar en un CD i executar-lo abans d'arrencar el Sistema Operatiu (quan l'ordinador s'engegui prem F8, així podràs canviar l'ordre d'arrencada)
 T'anirà molt més bé aquesta versió que la de Linux.La pots baixar d'aquí:

 [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

 A10!

David

---

### Post by papapep on 2008-11-25
A veure, esteu posant el carro davant els bous. No l'emboliquem, si us plau. Ara hem de saber què té, i després ja veurem com es fa, d'acord?

---

### Post by jinglada on 2008-11-25
Gràcies per les ràpides respostes. Vet ací el que tinc:

joan@joan-laptop:~$ sudo fdisk -l

Disc /dev/sda: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a645369

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1       29666   238292113+  83  Linux
/dev/sda2           29667       30401     5903887+   5  Estesa
/dev/sda5           29667       30401     5903856   82  Intercanvi Linux / Solaris

Quedo a l'espera dels vostres consells,
Joan

---

### Post by Satboy on 2008-11-26
> **papapep said:**
> A veure, esteu posant el carro davant els bous. No l'emboliquem, si us plau. Ara hem de saber què té, i després ja veurem com es fa, d'acord?

 Bon dia!
 Ho sento **Papapep**, jo només volia ajudar en **jinglada**. :(:(

 A10!

David

---

### Post by jinglada on 2008-11-26
> **Satboy said:**
> Ho sento **Papapep**, jo només volia ajudar en **jinglada**. :(:(

Gràcies Satboy! 

Papapep, amb el que he enviat que creus que he de fer ara?

---

### Post by papapep on 2008-11-26
Enganxa el que et surti en fer:

```
cat /etc/fstab
```

---

### Post by jinglada on 2008-11-26
> **papapep said:**
> Enganxa el que et surti en fer:

```
cat /etc/fstab
```

joan@joan-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7c97fe75-576a-4e19-a86e-06f45a077fb2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5de44525-5115-4e83-8af3-9af0102ab58b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by papapep on 2008-11-26
Doncs de tot el que has fet fins ara, se'n desprèn:

```
Dispositiu Arrenc. Inici Final Blocs      Id Sistema
/dev/**sda1**  *       1     29666 238292113+ 83 **Linux**
/dev/sda2          29667 30401 5903887+    5 Estesa
/dev/**sda5**          29667 30401 5903856    82 **Intercanvi** Linux / Solaris

```

tens una particions amb dades, sda1 i la d'intercanvi, sda5.

```
# /dev/sda1
UUID=... **[COLOR="Red"]/[/COLOR]** ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=... none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0 
```

Com que ho tens tot a una sola partició (sda1), si vols crear-ne una de nova a banda per a les dades, normalment el /home, el primer que et caldrà és decidir quant vols dedicar-hi de la actual partició "global". 
Quan ho hagis decidit (normalment entre 20 i 40 Gb serien més que suficient, a no ser que siguis del que instal·la tot el que li passa pel davant), et caldrà fer servir l'eina adeqüada.
Tal i com t'han comentat abans, el GParted (al menú de l'Ubuntu surt com a "Editor de particions"), és una de les eines més fiables per la tasca que vas a fer.
Primer et caldria redimensionar (o sigui, empetitir) la partició sda1, per deixar espai a la nova que vols crear. Un cop fet, has de crear la nova partició a l'espai buit que has creat, formatar-la a algun sistema de fitxers (normalment ext3), i ficar-ho dins el fstab per a que el munti cada cop que engeguis l'ordinador. 
No sé si tot això et sona molt complicat, o no, però no pateixis, si es fa pas a pas és molt més fàcil del que sembla explicant-ho :-)

Pas 1.- Per editar les particions d'un sistema, cal treballar amb les particions desmuntades. O sigui, que no pots treballar amb l'editor de particions sobre el mateix sistema que l'està executant. Ergo, et cal un livecd d'Ubuntu, per exemple, per fer-lo arrencar a l'ordinador i poder editar-ne les particions del disc dur.
Quan arrenquis amb el livecd posat, si engegues l'editor de particions que trobaràs a Sistema > Administració, veuràs (si tot va com ha d'anar) les particions existents al teu disc dur, i podràs fer el que t'he comentat abans. Redimensionar sda1 i crear-ne una de nova a l'espai buit que deixis.

Què et sembla si provem fins aquí?

**[COLOR="Red"]ATENCIÓ:[/COLOR]** no sol haver problemes en aquest procés, però si tens dades que no vulguis perdre a l'ordinador, abans de començar fes-ne una còpia de seguretat, per assegurar la jugada.

---

### Post by jinglada on 2008-11-26
Hola papapep,
he hagut d'entrar en el setup per dir-li que arranqués des del CD i després de particionar ho he hagut de tornar a canviar a HD.

Aquí tens el resultat:
----------------------------------
joan@joan-laptop:~$ sudo fdisk -l
[sudo] password for joan: 

Disc /dev/sda: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a645369

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1        7649    61440561   83  Linux
/dev/sda2           29667       30401     5903887+   5  Estesa
/dev/sda3            7650       17848    81923467+  83  Linux
/dev/sda4           17849       29666    94928085    7  HPFS/NTFS
/dev/sda5           29667       30401     5903856   82  Intercanvi Linux / Solaris

Les entrades a la taula de particions no estan en l'ordre del disc
joan@joan-laptop:~$ 
--------------------------------------

He afegit dues particions, una linux i l'altra ntfs perquè tinc un HD extern de quan tenia el mac, que és ntfs i he pensat que potser m'anirà bé.

Està bé així ho creus que ho hauria de canviar? 
Si em dius que està bé ja posaré el SOLVED.
Bona nit i gràcies,
Joan

---

### Post by papapep on 2008-11-27
El que comentes del disc extern NTFS no ho acabo d'entendre. Si és extern, quan el connectis ja es muntarà, no cal pas que tinguis una partició feta al disc local per a accedir-hi. M'explico?

A banda, encara et cal definir a /etc/fstab els punts de muntatge de la/les noves particions, per que t'aparegui l'espai com a disponible quan engeguis l'ordinador. Però primer aclarim el tema de la partició NTFS que, tal i com ho expliques, no et fa falta per a res.

---

### Post by jinglada on 2008-11-27
Tens raó pel que fa a la NTFS. Em vaig fer un embolic (segur que no eren hores de fer particions ;)). De fet el disc extern que tinc és de format HFS que és el format del Mac i es munta automàticament:
-------------------
joan@joan-laptop:~$ sudo fdisk -l
...
Disc /dev/sdb: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

El disc /dev/sdb no conté una taula de particions vàlida
joan@joan-laptop:~$ 
-----------------

Llavors què he de fer? La formato com ext3? També pot ser interessant tenir dues particions per a classificació de dades per separat, oi?

PD. aquests lapsus també et fan aprendre;)

---

### Post by papapep on 2008-11-27
> PD. aquests lapsus també et fan aprendre

Ei, Joan, que només no s'equivoquen els que no fan res, o sigui que endavant i crits! :-)

Respecte el que comentes de tenir una o dues o les particions que sigui, doncs és un criteri bastant personal. Si fos per un servidor hi hauria certs criteris que es podria seguir, però essent un sistema personal, jo tampoc em complicaria gaire la vida.
El fet de tenir, per exemple, el /home separat de la resta et permet estalviar-te problemes en actualitzar versions. Més divisions del disc tampoc té massa sentit, però això no vol dir que no puguis fer-ho, el disc és teu ;-)

I sí, ara et cal formatar-ho a ext3 (la/les extensions que siguin) amb aquesta ordre:

```
mkfs.ext3 /dev/sdN
```

sent N el número de partició que vulguis formatar. _Molt de compte en no equivocar-te de partició_, que si ho fas amb una que no toca ho perds tot...

Un cop fet això, hauràs de copiar, per exemple, el /home a la nova partició i canviar les definicions a /etc/fstab per a que el nucli sàpiga on tens el nou /home a l'hora d'arrencar.

---

### Post by jinglada on 2008-11-27
Hola Josep,

> **papapep said:**
> Ei, Joan, que només no s'equivoquen els que no fan res, o sigui que endavant i crits! :-)
Un poeta, amic meu, però de la "quinta" del meu pare, diu que els que s'equivoquen de veritat són precisament aquells que no fan res.

> Respecte el que comentes de tenir una o dues o les particions que sigui, doncs és un criteri bastant personal. Si fos per un servidor hi hauria certs criteris que es podria seguir, però essent un sistema personal, jo tampoc em complicaria gaire la vida.
El fet de tenir, per exemple, el /home separat de la resta et permet estalviar-te problemes en actualitzar versions. Més divisions del disc tampoc té massa sentit, però això no vol dir que no puguis fer-ho, el disc és teu ;-)

I sí, ara et cal formatar-ho a ext3 (la/les extensions que siguin) amb aquesta ordre:

```
mkfs.ext3 /dev/sdN
```

sent N el número de partició que vulguis formatar.

He entrat altre cop al GParted i he esborrat la partició NTFS i l'he afegida a la ext3 i també l'he formatada amb el GParted.

--------------------------------------
joan@joan-laptop:~$ sudo fdisk -l

Disc /dev/sda: 250.0 GB, 250059350016 octets
255 heads, 63 sectors/track, 30401 cylinders
Units = cilindres of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a645369

Dispositiu Arrenc.   Inici         Final    Blocs    Id  Sistema
/dev/sda1   *           1        7649    61440561   83  Linux
/dev/sda2           29667       30401     5903887+   5  Estesa
/dev/sda3            7650       29666   176851552+  83  Linux
/dev/sda5           29667       30401     5903856   82  Intercanvi Linux / Solaris

Les entrades a la taula de particions no estan en l'ordre del disc
joan@joan-laptop:~$ 
------------------------------------

He provat de crear-hi una carpeta i no ho permet com tampoc copiar-hi fitxers, diu: *No es pot copiar la carpeta «xxx» perquè no teniu permís per a crear-la en la destinació.*

> Un cop fet això, hauràs de copiar, per exemple, el /home a la nova partició i canviar les definicions a /etc/fstab per a que el nucli sàpiga on tens el nou /home a l'hora d'arrencar.

Em pots dir com es fa això?
Gràcies,
Joan

---

### Post by jinglada on 2008-11-28
> **jinglada said:**
> Hola Josep,
He provat de crear-hi una carpeta i no ho permet com tampoc copiar-hi fitxers, diu: *No es pot copiar la carpeta «xxx» perquè no teniu permís per a crear-la en la destinació.*
Em pots dir com es fa això?
Gràcies,
Joan

He provat amb el Nautilus i ja he pogut copiar i crear fitxers i directoris.
El que ara em passa és que els directoris, subdirectoris i fitxers copiats del disc extern, que són proteccions del Mac, queden com a propietari i grup propietari "root". Com es pot fer un chmod i chgrp genèric per a directoris, subdirectoris i fitxers?

---

### Post by papapep on 2008-11-28
Fent:

```
sudo chown josepmaria:josepmaria /eldirectoriquevulguis/ -R
```

la -R fa que sigui recursiu a **tot** el que sigui per sota del directori que especifiques, i suposant que el teu usuari és *josepmaria*.

Tens un petit manual d'ordres de terminal [aquí]("https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes"), que igual t'ajudarà amb aquestes coses.

---

### Post by jinglada on 2008-11-29
> **papapep said:**
> 
Un cop fet això, hauràs de copiar, per exemple, el /home a la nova partició i canviar les definicions a /etc/fstab per a que el nucli sàpiga on tens el nou /home a l'hora d'arrencar.

He tret el SOLVED perquè em falta fer l'últim pas. Em podeu ajudar?
He tornat a posar el SOLVED i amb data 2/12/08 he obert un altre fil amb el títol posar "/home a partició per a dades"

---

