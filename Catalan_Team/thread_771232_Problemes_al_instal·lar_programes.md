---
title: "Problemes al instal·lar programes"
date: 2008-04-27
forum: Catalan Team
---

### Post by auska1714 on 2008-04-27
Bones,

mireu, em trobo que quan vull instal·lar programes i/o plugins (no se si s'escriu aixi) em diu que la llista no esta actualitzada. L'actualitzo i em torna a dir el mateix. I aixi infinitament. Que puc fer?

Gràcies per avançat,

**Auska**

---

### Post by papapep on 2008-04-27
> quan vull instal·lar programes i/o plugins

Com els intentes instal·lar? Enganxa'ns la ordre exacta o una impressió de pantalla per veure exactament la situació.

---

### Post by auska1714 on 2008-04-27
aquí tens les captures de pantalla que em demenaves, la primera es d'un plugin des del firefox i les altres dos d'instalar programes a partir de: aplicacions; afexeix/suprimeix...

---

### Post by papapep on 2008-04-27
Probablement tot el mal ve del mateix lloc, que no tens la llista de paquets actualitzada. Assumeixo que la connexió a internet et funciona correctament, aleshores potser hauries de canviar els servidors que tens pels repositoris.
Enganxa si us plau el contingut del sources.list. Fes a un terminal:

```
cat /etc/apt/sources.list
```

i enganxa aquí el seu contingut.

---

### Post by jmaspons on 2008-04-27
Mira quines fonts de programari tens activades. Per instal·lar el flashplugin-nonfree cal activar el repositori multiverse.

---

### Post by auska1714 on 2008-04-27
em surt:

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

i continua sense deixar-me

---

### Post by auska1714 on 2008-04-27
> **jmaspons said:**
> Mira quines fonts de programari tens activades. Per instal·lar el flashplugin-nonfree cal activar el repositori multiverse.

I on ho he de mirar això?

---

### Post by SiscoGarcia on 2008-04-27
Ves a Sistema>Administració>Fonts de programari. Allà hi trobaràs les diverses fonts (main, universe, restricted, multiverse).

---

### Post by pespin on 2008-04-27
Tens tots els repositoris desactivats. Ja has actualitzat a Hardy o segueixes a Gutsy?

---

### Post by CarlesOriol on 2008-04-28
Eps?

Estem parlant de plugins del firefox? Pot ser que tinguis una ubuntu de 64 bits?

---

### Post by auska1714 on 2008-04-28
Anava amb el 7.10 i em vaig passar a hardy. Però al teniri molts problemes vaig tornar a instal·lar el 7.10 utilitzant el mateix que avants. 

Sisco, sobre el que em deies, no se que passa pero no tinc actibada l'icona de fonts del programari

---

### Post by SiscoGarcia on 2008-04-28
> Sisco, sobre el que em deies, no se que passa pero no tinc actibada l'icona de fonts del programari

Ara ja vaig amb hardy :) però si no recordo malament (ja fa temps que no ho tocava amb gutsy) és al mateix lloc, si fa no fa, és a dir, a Sistema>Administració>Fonts de programari. Si m'equivoco i no hi és, jo remenaria una mica, però crec que hi hauria de ser.

Sort!

---

### Post by auska1714 on 2008-04-28
ho hauria de activar però no em deixa

---

### Post by SiscoGarcia on 2008-04-28
També hi pots arribar pel Synaptic. Això és Sistema>Administració>Gestor de paquets Synaptic i un cop obert el Synaptic (et demana contrasenya) ho tens a Paràmetres>Dipòsits.

És el mateix però no és una via directa.

---

### Post by auska1714 on 2008-04-28
Ja està ha he activat les fonts i ara ja puc instal·lar el que vulgui, meci ;)

---

### Post by auska1714 on 2008-04-28
no se que passa però no em deixa posar el post com a resolt, no em surt l'opció

---

### Post by SiscoGarcia on 2008-04-28
> **auska1714 said:**
> no se que passa però no em deixa posar el post com a resolt, no em surt l'opció

No t'hi capfiquis, han desactivat aquesta opció i sembla que estem fent córrer una versió "beta" del fòrum però quan sigui estable es podrà tornar a fer. :)

---

