---
title: "M'han desparegut icones i altres !!"
date: 2007-12-26
forum: Catalan Team
---

### Post by lluisalguero on 2007-12-26
Hola amics,
resulta que avui després d'un parell de dies sense connectar el portàtil, a l'escriptori m'han desaparegut el fons d'escriptori que tenia, així també com les icones de les particions que tenia (la resta d'icones hi son totes)

He anat al menú Llocs-> Ordinador i allà tampoc em surten les particions.

Hi ha alguna forma de restaurar tot això?

Gràcies,
Lluís

P.D.: també m'he adonat que les regles dels missatges que tenia al Thunderbird se les "salta a la torera" :confused:

---

### Post by pespin on 2007-12-26
Pots donar més informació sobre les particions? Enganxa el fstab per exemple.


També mira si el Ubuntu et veu els dispositius (mira a /dev/sd*) i també pots mirar si tens muntades les particions amb "df -Th".

Suposo que el fons et surt canviat perquè tenies la imatge en una de les particions que ara no se't munten

---

### Post by lluisalguero on 2007-12-26
El fstab es aquest:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=8e84d134-32f4-4ea4-ba8b-b7b3878667fc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=8208BEE408BED5FF /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=7038585538581C82 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=76969580-fc53-4ed4-90ee-7d7b63ee5f10 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

a /deb/ hi puc trobar:

-sdc0
-sda
-sda1
-sda2
-sda3
-sda4

i el fons,crec que si, estaba a un altra partició

si necesiteu alguna dada més, només teniu que demanar-la. Com a informació dir que tinc
- 1 partició amb finestres XP
- 1 partició amb l'Ubuntu 7.10
- 1 partició amb arxius (fotos, documents, etc)

---

### Post by lluisalguero on 2007-12-26
lluis@lluis-laptop:~$ df -Th
S. fitxers   Tipus    Tamany En ús Lliure %Ús Muntat a
/dev/sda4     ext3     20G   15G  3,4G  82% /
varrun       tmpfs    506M  100K  506M   1% /var/run
varlock      tmpfs    506M     0  506M   0% /var/lock
udev         tmpfs    506M   84K  506M   1% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
lrm          tmpfs    506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
lluis@lluis-laptop:~$

---

### Post by pespin on 2007-12-27
Bé. Anem per passos:

Tens una partició sda4 (ext3) com a arrel del sistema de fitxers, que està muntada.

sda3 és el swap.

llavors ens queden el sda1 i sda2 que no estan muntats. 


Pots provar amb aquesta, a veure que et diu (muntar-les totes d'una sola tacada)

```
mount -a
```

Qualsevol error enganxa'l aquí.

Una per una:
```

mount /dev/sda1

mount /dev/sda2
```
En principi no cal especificar lloc de muntatge perquè ja està especificat al fstab.

---

### Post by papapep on 2007-12-27
Jo, ara, no sé quina és la sol·lució al problema, però crec que no aneu ben orientats.
Si li carrega l'escriptori és que la partició on té el /home (que en aquest cas és /dev/sda4), li carrega correctament. A banda, /dev/sda1 i /dev/sda2 tenen pinta de ser un disc extern, ja que comença per /media el punt de muntatge. Quants discs durs tens, i de quin tipus són, Lluís?

Té tot l'aspecte de ser un problema amb els permisos de l'usuari o similar.
Lluís, abans de apagar el portàtil (la última vegada que et sortia el que ara trobes a faltar) vas instal·lar o desinstal·lar algun programari? Pensa que, normalment, les coses no passen soles... :-)

---

### Post by lluisalguero on 2007-12-27
Com va dir Jack el desbudellador...anem per parts

- Per art de màgia, ara al ficar en marxa el portàtil, sense jo tocar res, han tornat a aparèixer les dos particions que havien desaparegut.

- Respecte a instalar/desinstalar programari, només les actualitzacions del que ja tinc instalat (l'avís que surt periòdicament a la barra superior).

- No tinc cap disc extern connectat i només tinc un disc dur amb 3 particions (XP, Ubuntu i Fitxers)

- Una cosa que he fet amb la configuració d'usuari ha estat que em demanés usuari i pass per entrar, abans ho tenia amb l'entrada directa.

- Si necessiteu algun altra informació, només teniu que demanar-la

Gràcies per el vostre suport,
Lluís

---

### Post by pespin on 2007-12-27
> Si li carrega l'escriptori és que la partició on té el /home (que en aquest cas és /dev/sda4), li carrega correctament. A banda, /dev/sda1 i /dev/sda2 tenen pinta de ser un disc extern, ja que comença per /media el punt de muntatge. Quants discs durs tens, i de quin tipus són, Lluís?

Potser m'equivoco, pero si totes les particions són sda*, es deuen referir al mateix disc, i com només n'hi ha un, dubto que sigui extraible :)

---

### Post by papapep on 2007-12-27
En teoria, evidentment, és així, però com que a la pràctica passen moltes coses millor saber què hi ha a la realitat.

---

### Post by lluisalguero on 2007-12-27
Us aseguro que només tinc un HD de 120 Gb en les 3 particions abans esmentades :)

---

### Post by pespin on 2007-12-28
Has dit que ara ja et funciona bé per això no?

Quan et torni a passar prova a fer el que he posat abans :)

A partir d'aquí si falla podrem veure l'error i solucionar-ho

---

### Post by lluisalguero on 2007-12-28
> **pespin said:**
> Has dit que ara ja et funciona bé per això no?

Quan et torni a passar prova a fer el que he posat abans :)

A partir d'aquí si falla podrem veure l'error i solucionar-ho

Això faré, i ja de passada si me n'adono miraré si em fa alguna cosa extranya...

---

