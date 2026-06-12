---
title: "[SOLVED] Problemes d'Actualització Amb l'Intrèpid (KDE m'invaeix!)"
date: 2008-11-03
forum: Catalan Team
---

### Post by LitusMayol on 2008-11-03
Bones!

Jo espero amb ànsies la *Intrepid*... Si encara! hehe Tinc un problema i és que el **Synaptic** em presenta aquest missatge tan i tan maco (veure adjunt). A l'hora d'actualitzar em vol desinstal·lar tots els programes típics de GNOME (**Pidgin, GnomeBaker**...) i em vol instal·lar KDE (em sembla que s'aprecia a la captura).

Algú sap perquè pot ser? Algú em pot ajudar...?



[COLOR="SlateGray"](**Orestes**, sé que tu no veus el problema doncs KDE és el millor del millor, però encara em quedo amb GNOME hehehe ;) )[/COLOR]

---

### Post by SiscoGarcia on 2008-11-03
> **LitusMayol said:**
> BA l'hora d'actualitzar em vol desinstal·lar tots els programes típics de GNOME (**Pidgin, GnomeBaker**...) 

Perdona Litus però a la captura que ens passes jo no veig que et vulgui desinstal·lar els programes que dius; només veig que vol instal·lar-te KDE. Potser el tenies instal·lat ara i per això t'ho diu a l'hora d'actualitzar-se?

---

### Post by LitusMayol on 2008-11-03
Tinc paquets concrets de KDE instal·lats (per exmple els necessaris per a l'**Amarok**, el de català, etc...).

Però a la captura anterior no posava "actualitzar", posava "instal·lar". Són paquets que de moment no necessito (perquè vull jo els icones de l'oxygen? :S ). No entenc perquè fa això. 


(a la nova captura es veu el que deia de la supressió de paquets)

---

### Post by PatrickVogeli on 2008-11-03
ensenyans el teu /etc/apt/sources.list

salut

---

### Post by LitusMayol on 2008-11-03
> **PatrickVogeli said:**
> ensenyans el teu /etc/apt/sources.list


Uiii... això sóna a *estriptis*! xD


Aquí el teniu:
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.grn.cat/ubuntu/ hardy main restricted
deb-src http://ubuntu.grn.cat/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.grn.cat/ubuntu/ hardy-updates main restricted
deb-src http://ubuntu.grn.cat/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ubuntu.grn.cat/ubuntu/ hardy universe
deb-src http://ubuntu.grn.cat/ubuntu/ hardy universe
deb http://ubuntu.grn.cat/ubuntu/ hardy-updates universe
deb-src http://ubuntu.grn.cat/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.grn.cat/ubuntu/ hardy multiverse
deb-src http://ubuntu.grn.cat/ubuntu/ hardy multiverse
deb http://ubuntu.grn.cat/ubuntu/ hardy-updates multiverse
deb-src http://ubuntu.grn.cat/ubuntu/ hardy-updates multiverse

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
deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ubuntu.grn.cat/ubuntu/ hardy-security main restricted
deb-src http://ubuntu.grn.cat/ubuntu/ hardy-security main restricted
deb http://ubuntu.grn.cat/ubuntu/ hardy-security universe
deb-src http://ubuntu.grn.cat/ubuntu/ hardy-security universe
deb http://ubuntu.grn.cat/ubuntu/ hardy-security multiverse
deb-src http://ubuntu.grn.cat/ubuntu/ hardy-security multiverse




##POTINEJANT


##Aquests són els repositoris del Avant Windows Navigator
# deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
# deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main

##Aquests són els repositoris del Dropbox
# deb http://www.getdropbox.com/static/ubuntu hardy main
# deb-src http://www.getdropbox.com/static/ubuntu hardy main

##Aquest són els repositoris del DiscWrapper
# deb http://apt.wxwidgets.org/ hardy-wx main

# deb http://getdeb.masio.com.mx/ getdeb/
# deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

---

### Post by PatrickVogeli on 2008-11-03
veient tot el que hi tens posat, es posible que hagis creat algun problema. Jo treuria els repositoris no oficials, faria un apt-get update i tornaria a provar, a veure que fa

EDITO: oblida el que t'he dit, estic empanat. Fes un sudo apt-get install ubuntu-desktop, a veure si despres va millor. Si no va, jo diria que alguna cosa que t'has instal·lat et pot estar donant problemes. De totes formes no se si soc jo o que, pero tinc la sensacio de que actualitzar de hardy a intrepid esta donant més problemes que altres cops.

salut

---

### Post by LitusMayol on 2008-11-03
A veure... Mireu això:

```
litus@mayolets-desktop:~$ sudo apt-get install ubuntu-desktop
[sudo] password for litus: 
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
S'està llegint la informació d'estat... Fet
ubuntu-desktop ja es troba en la versió més recent.
0 actualitzats, 0 nous a instal·lar, 0 a eliminar i 0 no actualitzats.
litus@mayolets-desktop:~$ 
```


Aleshores he eliminat l'apartat de "*POTINEJANT*" del *source.list*. Tot seguit he fet el "*sudo apt-get update*". He anat a *Sistema>Administració>Gestor d'Actualitzacions* i tot segueix igual. Tinc el mateix problema... :(

---

### Post by indiosincracia on 2008-11-03
per a fer una actualització es suficient això:

> # deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

comenta "#" l'enrenou que tens, 
sudo apt-get update
sudo apt-get upgrade

no se el synaptic, però l'adept et mostra la posibilitat d'actualitzar la versió, en aquest punt.

---

### Post by LitusMayol on 2008-11-03
Ep familia!

Al final he apuntat (a mà...) quins paquets anava a desinstal·lar (per si de cas) i he actualitzat.

1h i escaig. De les actualitzacions més ràpides i sense problemes que he tingut. Fantàstic. L'únic problema que he tingut és que he hagut de tornar a redefinir la col·lecció de l'**Amarok** (fàcil: "*Reescaneja la col·lecció*").



Merci a tots de totes maneres!

(us adjunto una captureta de regal! :D )

---

