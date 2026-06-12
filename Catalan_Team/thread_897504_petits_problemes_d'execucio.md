---
title: "petits problemes d'execucio"
date: 2008-08-22
forum: Catalan Team
---

### Post by venusfenix on 2008-08-22
El tema es el següent:
perque hi han vegades que quan vaig a instalar nous programes, o vull executar el synaptics, desde els menus no puc, o sigui, l'aplicacio comença a executar-se pero s'acaba tancant, pero desde el terminal root, sempre s'executa.
potser que hagi instalat algun programa que doni problemes??

gracies,

---

### Post by papapep on 2008-08-22
Doncs probablement sigui problema de permisos, pel que comentes. 
Quan et passi no executis mai el programa com a usuari root, fes un "sudo" i a veure què et diu.

> potser que hagi instalat algun programa que doni problemes??


Per sort, això no és windows, i aquestes coses són terriblement difícils que passin.

---

### Post by venusfenix on 2008-08-22
he fet al terminal sudo synaptics i funciona, pero desde el menu, na' de na' com diuen a andalusia.
per altre banda i no se si son sintomes del mateix problema, quan vull afegir algun programa, normalmente, s'executa correctament i despres de fer la triar de programes, despres a l'aplicar, al instalar, es queda com penjat (?) es normal?? el cursor va fent el rellotje pero no passa res, i ni es tancat ni s'instalen el programes.

com vindre tot de l'ho mateix??

gracias,

---

### Post by papapep on 2008-08-22
Evidentment, no és normal, només faltaria. Ara bé, de la causa no en tinc ni idea. No tinc prou elements per valorar. Calen més dades.
Des de quan et passa? has fet alguna cosa que recordis que hagi pogut afectar el funcionament del sistema de gestió de paquets? quina versió tens instal·lada de l'ubuntu? què tens dins el fitxer /etc/apt/sources.list??

---

### Post by venusfenix on 2008-08-22
l'he instal·lat fa dos dies, i tinc el ubuntu 8.04 64 bits.
des de el primer dia que estic mirant quines aplicacions necessitaré i estis cada dia instal·lant de noves, no recordo quina va ser l'aplicació que vaig instal·lar però n'hi han unes quantes.


gracies,

El contingut del fitxer:

#deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release amd64 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by papapep on 2008-08-22
Doncs el sources.list es veu normal.

El que faria jo és provar des del terminal a veure què fa:

```
sudo aptitude update
```

i un cop estigui

```
sudo aptitude safe-upgrade
```

i a veure quins missatges mostra.

---

### Post by venusfenix on 2008-08-22
sembla tot correcte, l'unica cosa es al executar sudo safe-upgrade surt un comentari:
sudo: unable to resolve host shuttle
pero la resta es OK.

shutlle = portatil

gracies,

---

### Post by papapep on 2008-08-22
Enganxa'ns els missatges complerts, si us plau. Si són massa grans, fes-ho amb un fitxer adjunt.

---

### Post by venusfenix on 2008-08-22
Buenas!!!
degut a altres problemes aliens, m'he vist obligat a començar de nou....
snif...snif...
igualment, moltes merces!!!!
potser quan torni al mateix punt d'ara en unes hores, torno a fer la consulta.

gracies,

---

### Post by papapep on 2008-08-22
Bé, en tot cas, això sempre et servirà d'experiència. Ara el que hauries de fer és estar molt atent a cada passa que facis, per si se't torna a generar el problema saber d'on pot provenir.

---

