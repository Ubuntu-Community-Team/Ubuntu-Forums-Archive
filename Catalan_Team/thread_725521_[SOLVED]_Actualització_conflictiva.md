---
title: "[SOLVED] Actualització conflictiva"
date: 2008-03-15
forum: Catalan Team
---

### Post by lo gambusí on 2008-03-15
Salut!!

Fa un temps que no actualitzava, per raons de temps, i ara que m'hi he decidit em dóna un [missatge d'error]("http://img247.imageshack.us/img247/3936/capturaqk2.png"). Li dic que me face l'actualització parcial, però llavors me diu[ això altre.]("http://img221.imageshack.us/img221/7017/captura1iw9.png")

I d'aquí no mo'n sortim.

Alguna idea? Gràcies!

---

### Post by papapep on 2008-03-15
El primer que hauries de fer és analitzar quina de les tres causes del missatge d'error és la que es pot aplicar al teu problema.

En funció de quina sigui, doncs es poden fer diverses coses.

---

### Post by lo gambusí on 2008-03-16
Ja, però és que no en tinc ni idea... :|

---

### Post by CarlesOriol on 2008-03-16
copia'ns el teu sources.list de /etc/apt

Crec que tens alguna font que t'està causant el problema.

---

### Post by lo gambusí on 2008-03-18
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) gutsy main
deb [http://www.bashterritory.com/pytube/releases](http://www.bashterritory.com/pytube/releases) /
deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/
#AWN
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator

Això?

---

### Post by papapep on 2008-03-18
> deb [http://elisa.fluendo.com/packages](http://elisa.fluendo.com/packages) gutsy main
deb [http://www.bashterritory.com/pytube/releases](http://www.bashterritory.com/pytube/releases) /
deb [http://ubuntu.org.ua/](http://ubuntu.org.ua/) getdeb/
#AWN
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) gutsy avant-window-navigator 

Jo provaria a comentar totes aquestes entrades, que no són repositoris oficials, i després a fer un **aptitude update** i un **aptitude safe-upgrade** a veure si ara ja no es queixa.

No s'ha de perdre mai de vista que afegir fonts de programari no oficials és un risc i ens pot portar conflictes amb els paquets.

---

### Post by lo gambusí on 2008-03-18
comentar significava posar un # davant de cada línia, no?

---

### Post by papapep on 2008-03-18
Si senyor.

---

### Post by lo gambusí on 2008-03-18
a poc a poc vaig aprenent :P

bé, ho he fet i m'ha desaparegut la icona de notificació d'actualitzacions, per tant suposo que ho hem solucionat, no? :)

---

### Post by papapep on 2008-03-18
Hauries d'executar el que t'he dit abans (com a mínim la primera) per sincronitzar la base de paquets amb els repositoris.

---

### Post by lo gambusí on 2008-03-18
sí, sí, ja ho havia fet.

gràcies, un cop més!!

---

