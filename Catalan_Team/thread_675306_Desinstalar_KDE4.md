---
title: "Desinstalar KDE4"
date: 2008-01-22
forum: Catalan Team
---

### Post by lluisalguero on 2008-01-22
Com a suggeriment de papapep, obro aquest fil per a que gent com jo que hagi provat el KDE4, vulgui fer una neteja del seu sistema i continuar amb el Gnome.

Les instruccions que vaig seguir son (crec) aquestes:

[http://www.cesarius.net/como-instalar-kde-40-en-kubuntu-710/](http://www.cesarius.net/como-instalar-kde-40-en-kubuntu-710/)

Si necessiteu alguna dada més, aquí estem...

Gràcies per endavant

---

### Post by papapep on 2008-01-22
Ostres, ostres, ostres.....a veure.
Jo no sóc KDE-aire, com ja sabreu i, per tant, potser seria millor que algú que en fos s'ho mirés, però per començar i sense fer cap destrossa seria bo veure què diu un:

```
apt-cache show kde4-core
```

bàsicament per veure quines dependències té.

---

### Post by lluisalguero on 2008-01-22
lluis@lluis-laptop:~$ apt-cache show kde4-core
Package: kde4-core
Priority: optional
Section: kde
Installed-Size: 36
Maintainer: Terence Simpson <stdin@stdin.me.uk>
Architecture: all
Version: 3.3~gutsy1~ppa1
Suggests: kde-i18n (>= 4:4.0.0)
Depends: kdebase-kde4 (>= 4:4.0.0), kdebase-workspace (>= 4:4.0.0), kdebase-runtime (>= 4:4.0.0), kdelibs5 (>= 4:4.0.0), kdepimlibs5 (>= 4:4.0.0)
Filename: pool/main/m/meta-kde4/kde4-core_3.3~gutsy1~ppa1_all.deb
Size: 2814
MD5sum: fa4da7aa6513c76b20e4b7f312158108
Description: the K Desktop Environment version 4 core modules
 KDE (the K Desktop Environment) is a powerful Open Source graphical
 desktop environment for Unix workstations. It combines ease of use,
 contemporary functionality, and outstanding graphical design with the
 technological superiority of the Unix operating system.
 .
 This metapackage includes the core official modules released with KDE4. This
 includes just the basic desktop (browser, file manager, text editor, control
 center, plasma, etc.) and important libraries and data.

Package: kde4-core
Priority: optional
Section: universe/kde
Installed-Size: 36
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Terence Simpson <stdin@stdin.me.uk>
Architecture: all
Source: meta-kde4
Version: 3.2~gutsy1
Depends: kdebase-kde4 (>= 4:4.0.0), kdebase-workspace (>= 4:4.0.0), kdebase-runtime (>= 4:4.0.0), kdelibs5 (>= 4:4.0.0), kdepimlibs5 (>= 4:4.0.0)
Suggests: kde-i18n (>= 4:4.0.0)
Filename: pool/universe/m/meta-kde4/kde4-core_3.2~gutsy1_all.deb
Size: 2870
MD5sum: 988b25ab58c202fa6b2a376674009812
SHA1: 350e8a3e985874a13c81a935fd0f42ca3c747d60
SHA256: 0dc05bf62f2a9b87fee1c131c866fb17a39937459b4147228dca15a1707c9880
Description: the K Desktop Environment version 4 core modules
 KDE (the K Desktop Environment) is a powerful Open Source graphical
 desktop environment for Unix workstations. It combines ease of use,
 contemporary functionality, and outstanding graphical design with the
 technological superiority of the Unix operating system.
 .
 This metapackage includes the core official modules released with KDE4. This
 includes just the basic desktop (browser, file manager, text editor, control
 center, plasma, etc.) and important libraries and data.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by papapep on 2008-01-22
Jo provaria a fer el següent:

```
aptitude remove kde4-core kdebase-kde4 kdebase-workspace kdebase-runtime kdelibs5 kdepimlibs5 
```

**[COLOR="Red"]Però no acceptis[/COLOR]**, només és per veure si intenta esborrar més paquets a banda d'aquests.
Per cert, tu tenies KDE abans de posar el KDE4 o feies servir Gnome?

---

### Post by lluisalguero on 2008-01-22
> **papapep said:**
> Jo provaria a fer el següent:

```
aptitude remove kde4-core kdebase-kde4 kdebase-workspace kdebase-runtime kdelibs5 kdepimlibs5 
```

**[COLOR="Red"]Però no acceptis[/COLOR]**, només és per veure si intenta esborrar més paquets a banda d'aquests.
Per cert, tu tenies KDE abans de posar el KDE4 o feies servir Gnome?

No tenia cap versió anterior del KDE, només feia servir el gnome

Aquí tens la sortida...

lluis@lluis-laptop:~$ sudo aptitude remove kde4-core kdebase-kde4 kdebase-workspace kdebase-runtime kdelibs5 kdepimlibs5
[sudo] password for lluis:
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'està llegint la informació d'estat estesa       
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet 
Els paquets següents contenen errors.
  kde4libs-bin kdebase-runtime-bin-kde4 konqueror-kde4 konsole-kde4 
  kwin-kde4 libkonq5 
Els paquets següents no s'utilitzen i se suprimiran:
  dolphin-kde4 kappfinder-kde4 kdebase-bin-kde4 kdebase-workspace-bin 
  kdebase-workspace-data kdepasswd-kde4 kdepimlibs-data kfind-kde4 
  klipper-kde4 konqueror-nsplugins-kde4 ksysguard-kde4 ksysguardd-kde4 
  kwrite-kde4 libgpgme11 libplasma1 libpth20 libqimageblitz4 
  systemsettings-kde4 
Els paquets següents s'han apartat automàticament:
  tcl8.5 tk8.5 
Els paquets següents se suprimiran:
  kde4-core kdebase-kde4 kdebase-runtime kdebase-workspace kdelibs5 
  kdepimlibs5 
0 paquets actualitzats, 0 instal·lats, 24 a suprimir i 2 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'alliberaran 91,6MB.
No s'han trobat les dependències del paquets següents:
  kdebase-runtime-bin-kde4: Depén: kdebase-runtime però no es pot instal·lar.
                            Depén: kdelibs5 (>= 4:4.0.0-0ubuntu1~gutsy1) però no es pot instal·lar.
  libkonq5: Depén: kdebase-runtime però no es pot instal·lar.
            Depén: kdelibs5 (>= 4:4.0.0-0ubuntu2~gutsy1~ppa1) però no es pot instal·lar.
  kwin-kde4: Depén: kdebase-runtime però no es pot instal·lar.
             Depén: kdelibs5 (>= 4:4.0.0-0ubuntu2~gutsy1~ppa1) però no es pot instal·lar.
  konqueror-kde4: Depén: kdebase-runtime però no es pot instal·lar.
                  Depén: kdelibs5 (>= 4:4.0.0-0ubuntu2~gutsy1~ppa1) però no es pot instal·lar.
  konsole-kde4: Depén: kdebase-runtime però no es pot instal·lar.
                Depén: kdelibs5 (>= 4:4.0.0-0ubuntu2~gutsy1~ppa1) però no es pot instal·lar.
  kde4libs-bin: Depén: kdelibs5 (= 4:4.0.0-0ubuntu2~gutsy1~ppa1) però no es pot instal·lar.
Resolving dependencies...
Les accions següents resoldran les dependències:

Suprimeix els següents paquets:
kde4libs-bin
kdebase-runtime-bin-kde4
konqueror-kde4
konsole-kde4
kwin-kde4
libkonq5

Instal·la els següents paquets:
kdebase-bin-kde3 [4:3.5.8-2ubuntu3~gutsy1~ppa1 (gutsy)]

La puntuació és -1705

Accepteu la solució? [Y/n/q/?]

---

### Post by kukat on 2008-01-23
Jo també vull desinstalar-ho. Demane disculpes, crec que no encontraves el paquet Kubuntu-desktop per què vas instal.lar el kde4 i no és el mateix paquet.

Jo vaig instalar (abans de que sortira el kde4) el paquet kubuntu-desktop des del Synaptic. Si ara el desinstal.lo des del Synaptic no deu de passar res, no? 

Gràcies.  No es per què no m'agrade el KDE, es per què amb el Gnome hem sobra, i vull estalviar espai.:)

---

### Post by albert-I on 2008-02-02
M'agradaria saber de la gent que ha provat el KDE4, quants s'hi queden?

---

### Post by lluisalguero on 2008-02-02
Quan sapigue com desinstalar-lo sense fer malbé res....

---

### Post by CarlesOriol on 2008-02-02
> **albert-I said:**
> M'agradaria saber de la gent que ha provat el KDE4, quants s'hi queden?

Tots hem entes el kde4.0.0 com un escriptori no definitiu. Sols el començament del que és el kde4. I cal valorar-lo com a tal. 

Fa poc més d'un any i mig hi havia les primeres versions que s'aguantaven més de 10 minuts del compiz i mira ara.

---

