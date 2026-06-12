---
title: "Error a l'actualitzar"
date: 2008-07-15
forum: Catalan Team
---

### Post by LitusMayol on 2008-07-15
Bon dia!

Avui mentre actualitzava amb el gestor de paquets m'ha aparegut una finestreta amb el text següent:

> **S'ha produit un error**

Esproveeixen els detalls següents
```
E: linux-image-2.6.24-19-generic: el subprocés post-installation script retornà el codi d'eixida d'error 2
E: linux-ubuntu-modules-2.6.24-19-generic: problemes de dependències - es deixa sense configurar
E: linux-restricted-modules-2.6.24-19-generic: problemes de dependències - es deixa sense configurar
```



fa molt mala pinta... Algú sap què és i com solucionar-ho? 

Merci!

---

### Post by papapep on 2008-07-16
Fes un:

```
sudo apt-get -f install
```

a veure què et diu.

---

### Post by LitusMayol on 2008-07-18
Bon dia!

Doncs **papapep** això és el que em posa:

```
litus@mayolets-desktop:~$ sudo apt-get -f install
[sudo] password for litus: 
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
0 actualitzats, 0 nous a instal·lar, 0 a eliminar i 0 no actualitzats.
3 no instal·lats o eliminats completament.
After this operation, 0B of additional disk space will be used.
S'està configurant linux-image-2.6.24-19-generic (2.6.24-19.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-19.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-19.33 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: s'ha produït un error en processar linux-image-2.6.24-19-generic (--configure):
 el subprocés post-installation script retornà el codi d'eixida d'error 2
dpkg: problemes de dependències impedeixen la configuració de linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depèn de linux-image-2.6.24-19-generic; tot i així:
  El paquet linux-image-2.6.24-19-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-ubuntu-modules-2.6.24-19-generic (--configure):
 problemes de dependències - es deixa sense configurar
dpkg: problemes de dependències impedeixen la configuració de linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depèn de linux-image-2.6.24-19-generic; tot i així:
  El paquet linux-image-2.6.24-19-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-restricted-modules-2.6.24-19-generic (--configure):
 problemes de dependències - es deixa sense configurar
S'han trobat errors en processar:
 linux-image-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
litus@mayolets-desktop:~$ 

```

I a més a més, em surt el simbolet de dalt a la dreta amb el text:
```
**Cal que reinicieu l'ordinador**
```

i als pocs segons ha aparegut el simbolet conforme havia d'actualitzar. I he *clickat* i tenia 20 pquets per actualitzar. I al final d'aquesta actualització m'ha sortit el mateix error pel qual he obert aquest fil.

Merci! ;)

---

### Post by papapep on 2008-07-18
Podries tornar a provar a fer:

```
sudo aptitude update
sudo aptitude safe-upgrade
```

a vegades en actualitzar paquets queda alguna cosa penjada, i en tornar a fer-ho al cap d'uns dies es torna a posar a to. Per si sona la campana.

Si segueix fallant ja mirarem.

---

### Post by LitusMayol on 2008-07-20
Bones!

Després de fer:
```
sudo aptitude update
sudo aptitude safe-upgrade
```

M'ha demanat que reiniciés l'ordinador. Ho he fet. Després he agafat el **Pidgin** i li he fet un *purge* i un *install*(com que no hi havia actualitzacions i estic tenint problemes amb el missatger...). I el resultat ha sigut aquest en el *purgue*:
```
problemes de dependències - es deixa sense configurar
S'han trobat errors en processar:
 linux-image-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic

```

Això ho va repetint diverses vegades en línies molt semblant a aquesta:
```
 El paquet linux-image-2.6.24-19-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-restricted-modules-2.6.24-19-generic (--configure):
 problemes de dependències - es deixa sense configurar
S'han trobat errors en processar:
 linux-image-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic

```


I quan l'he instal·lat de nou m'ha fet una cosa semblant. Semblava que anava bé fins que...

```
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: s'ha produït un error en processar linux-image-2.6.24-19-generic (--configure):
 el subprocés post-installation script retornà el codi d'eixida d'error 2
dpkg: problemes de dependències impedeixen la configuració de linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depèn de linux-image-2.6.24-19-generic; tot i així:
  El paquet linux-image-2.6.24-19-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-ubuntu-modules-2.6.24-19-generic (--configure):
 problemes de dependències - es deixa sense configurar
dpkg: problemes de dependències impedeixen la configuració de linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depèn de linux-image-2.6.24-19-generic; tot i així:
  El paquet linux-image-2.6.24-19-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-restricted-modules-2.6.24-19-generic (--configure):
 problemes de dependències - es deixa sense configurar
S'està configurant pidgin (1:2.4.1-1ubuntu2.1) ...

S'han trobat errors en processar:
 linux-image-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
S'ha produït un error en la instal·lació del paquet. S'està intentant restablir.
S'està configurant linux-image-2.6.24-19-generic (2.6.24-19.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-19.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-19.33 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: s'ha produït un error en processar linux-image-2.6.24-19-generic (--configure):
 el subprocés post-installation script retornà el codi d'eixida d'error 2
dpkg: problemes de dependències impedeixen la configuració de linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depèn de linux-image-2.6.24-19-generic; tot i així:
  El paquet linux-image-2.6.24-19-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-restricted-modules-2.6.24-19-generic (--configure):
 problemes de dependències - es deixa sense configurar
dpkg: problemes de dependències impedeixen la configuració de linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depèn de linux-image-2.6.24-19-generic; tot i així:
  El paquet linux-image-2.6.24-19-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-ubuntu-modules-2.6.24-19-generic (--configure):
 problemes de dependències - es deixa sense configurar
S'han trobat errors en processar:
 linux-image-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
S'està llegint la llista de paquets... Fet          
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
S'està llegint la informació d'estat estesa      
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet
litus@mayolets-desktop:~$ 

```

Que en penseu?
Merci

(ho sento per la quantitat de terminal que *postejo*)

---

### Post by papapep on 2008-07-20
Prova amb:

```
sudo dpkg --configure -a
```

(com funcioni t'escabetxo, això ha sortit un munt de cops al fòrum... :-P)

---

### Post by LitusMayol on 2008-07-20
Ems embla que no... :(

```
litus@mayolets-desktop:~$ sudo dpkg --configure -a
[sudo] password for litus: 
S'està configurant linux-image-2.6.24-19-generic (2.6.24-19.36) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-19.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-19.33 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: s'ha produït un error en processar linux-image-2.6.24-19-generic (--configure):
 el subprocés post-installation script retornà el codi d'eixida d'error 2
dpkg: problemes de dependències impedeixen la configuració de linux-restricted-modules-2.6.24-19-generic:
 linux-restricted-modules-2.6.24-19-generic depèn de linux-image-2.6.24-19-generic; tot i així:
  El paquet linux-image-2.6.24-19-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-restricted-modules-2.6.24-19-generic (--configure):
 problemes de dependències - es deixa sense configurar
dpkg: problemes de dependències impedeixen la configuració de linux-ubuntu-modules-2.6.24-19-generic:
 linux-ubuntu-modules-2.6.24-19-generic depèn de linux-image-2.6.24-19-generic; tot i així:
  El paquet linux-image-2.6.24-19-generic encara no està configurat.
dpkg: s'ha produït un error en processar linux-ubuntu-modules-2.6.24-19-generic (--configure):
 problemes de dependències - es deixa sense configurar
S'han trobat errors en processar:
 linux-image-2.6.24-19-generic
 linux-restricted-modules-2.6.24-19-generic
 linux-ubuntu-modules-2.6.24-19-generic
litus@mayolets-desktop:~$ 

```

Mercid e nou **papapep**

---

### Post by papapep on 2008-07-20
No cal que tremolis al escriure...t'escabetxaré igual.... :-D


A veure si t'enxampo. Enganxa el que tens dins el /etc/apt/sources.list ....

---

### Post by LitusMayol on 2008-07-20
Aquí la tens! ;)


```
#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ad.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://ad.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ad.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://ad.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ad.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://ad.archive.ubuntu.com/ubuntu/ hardy universe
deb http://ad.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://ad.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ad.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://ad.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://ad.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://ad.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ad.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://ad.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

---

### Post by papapep on 2008-07-20
No tens cap repositori "raru", no funcionen les ordres de sempre....curiós....què has fet d'estrany aquests últims dies abans de que et petès??? (temes personals/escabrosos no calen, només respecte l´Ubuntu :-P)
I no se t'acudeixi dir que "res", que et veig a venir....ara et farem un 3r grau, com a Guantanamo....:-D

---

### Post by LitusMayol on 2008-07-20
> **papapep said:**
> No tens cap repositori "raru", no funcionen les ordres de sempre....curiós....què has fet d'estrany aquests últims dies abans de que et petès??? (temes personals/escabrosos no calen, només respecte l´Ubuntu :-P)
I no se t'acudeixi dir que "res", que et veig a venir....ara et farem un 3r grau, com a Guantanamo....:-D

Això és humor i la resta són parides! hehe



Doncs no et diré que re. No sé si recordes que m'havia carregat el Grub i que només m'hi apareixia l'**UbuntuStudio**?

Doncs per arreglar-ho vaig canviar cosetes del *menu.lst*. Bàsicament vaig agafar el Grub de l'**UbuntuStudio** i hi vaig fer un "*talla+enganxa*" amb els **Ubuntu**s que hi ha al Grub de l'**Ubuntu**... Però això hauria d'haver-la liat a l'**UbuntuS** no en aquest, no?

No ho sé... :S hehe

---

### Post by CarlesOriol on 2008-07-21
Menu.lst del Grub sols s'interpreta un, estigui a la partició que estigui.

Per tant el que has canviat era el que funcionava.

---

### Post by LitusMayol on 2008-07-21
La veritat,

no us preocupeu massa. És pura curiositat per saber què li passa. De fet, a casa m'han demanat que faci una reinstal·lació denomés **Ubuntu** (ara hi convivien **Ubuntu** i **UbuntuStudio** amb el d'en Guillem Portes).

Per tan tampoc és urgent. Però si es perquè vait  tocar el Grub... d'ara endavent aniré amb més de compte!


Merci!

---

