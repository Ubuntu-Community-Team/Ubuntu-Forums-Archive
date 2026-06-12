---
title: "[SOLVED] Problema amb l'actualització"
date: 2008-03-31
forum: Catalan Team
---

### Post by lo gambusí on 2008-03-31
Vos explico.

He instal·lat l'ubuntu a un company. Només tenia la 6.10, així que hem instal·lat esta i hem decidit actuaitzar després. Ho hem fet, i un cop instal·lat m'he dirigit a actualitzar la versió. 

Vaig a Sistema/Gestor d'actualitzacions i allí me dixa passar directament a la 7.04 o actualitzar fitxers. Li dic d'anar directament, i me dóna error segons el qual o no tinc connexió o no es pot accedir al servidor. 

Comprovo que sí tinc connexió, i faig lo sudo gedit de torn per mirar los repositoris. Los tinc en es.archive... i los dixo sense l'es, però seguix igual. Li dóno a actualitzar la resta d'arxius, és a dir, no a canviar de versió sinó a actualitzar els arxius d'esta, m'ho actualitza sense problema, i a l'hora de tornar a intentar actualitzar la versió me dóna lo mateix error.

Alguna idea?:):)

---

### Post by papapep on 2008-03-31
En un terminal, com no :-D :

```
sudo update-manager -c
```

Per cert, respecte els servidors, jo n'agafaria qualsevol menys els .es, i no és qüestió política, és que van de pena.

---

### Post by lo gambusí on 2008-04-01
Bé, he fet això i estic fent actualitzacions de la mateixa versió en la que esic, perquè a l'hora de passar a l 7.04 me dóna lo mateix error que ans: que o no hi ha connexió a internet o no hi ha los servidors. 

Ara quan acabe d'actualitzar-se canviaré lo lloc dels servidors, ara ho tinc en [http://archive.ubuntu.com](http://archive.ubuntu.com)

---

### Post by papapep on 2008-04-01
Seria interessant veure exactament tot el missatge que et mostra.

---

### Post by lo gambusí on 2008-04-01
Res, ja està... eren los servidors, passa que anit vaig dixar-me'n un d'espanyol i clar, se tornava boig.

Gràcies:)

---

### Post by SiscoGarcia on 2008-04-18
Bones,

Reobro aquest fil perquè sóc a la feina amb ordinadors duals (XP+ubuntu feisty 7.04) i no me'n surto a actualitzar-me a 7.10. Ja fa molts dies que ho intento i no hi ha manera. Les màquines són 11 dell dimension c521 amb processador amd athlon x2 de 64 bits.

L'última cosa que he provat és el que recomanes en aquest fil (sudo update-manager -c) i el terminal em dóna l'error que veieu a la captura adjunta. De tota manera llança el gestor d'actualitzacions i comença a actualitzar-se, però ràpidament s'atura i em mostra el següent missatge:

```
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-amd64/Packages.bz2 Sub-procés bzip2 ha retornat un codi d'error (2)
```

Alguna idea?

Gràcies.

---

### Post by papapep on 2008-04-18
Enganxa el teu /etc/apt/sources.list, si us plau. Has fet un "sudo aptitude update" abans de l'update manager?

---

### Post by SiscoGarcia on 2008-04-18
Bon dia, papapep,

Sí que he fet un "sudo aptitude update" seguit d'un "sudo aptitude upgrade", però res. Et passo el /etc/apt/menu.list d'on ja he tret l'automatix (ja fa dies), fins i tot l'he tret de les fonts de programari; és a dir, ho he fet de totes les maneres que se m'han acudit. En fi, allà va el /etc/apt/menu.list

> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

# deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

Ja diràs/direu.

---

### Post by papapep on 2008-04-18
Modifica tots els es.archive.... i treu-los el "es.". Deixa'ls com a "archive.ubuntu.com/etc..." (no és mania persecutòria, és que fallen més que una escopeta de canyes).
Torna a fer l'update, l'upgrade i a veure què tal.

---

### Post by SiscoGarcia on 2008-04-18
Ja ho he fet i semblava que avançava més que les altres vegades però s'ha quedat a:

> Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz) Sub-procés gzip ha retornat un codi d'error (1)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-amd64/Packages.bz2) Sub-procés bzip2 ha retornat un codi d'error (2)

Què vol dir?

---

### Post by papapep on 2008-04-18
Fes:

```
sudo rm /var/lib/apt/lists/partial/*
```

Després torna a fer l'update i demés.

---

### Post by SiscoGarcia on 2008-04-18
Acabo de provar-ho i no hi ha manera.

Una altra cosa, he observat que hi ha prefixes davant de les capçaleres dels repositoris que no entenc:
> 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-ca
Prem [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release


Què vol dir "Ign" i "Prem" i "Obj"?

---

### Post by papapep on 2008-04-18
Però l'aptitude update i l'upgrade t'han funcionat o no?

---

### Post by SiscoGarcia on 2008-04-18
Perdó papapep per no deixar les coses més clares. Sí les comandes aptitude update i aptitude upgrade han funcionat. El que ha fallat és l'update-manager que en llançar el gestor d'actualitzacions comença i aviat es queda penjat amb missatges com l'exposat abans.

També he forçat l'actualització amb sudo update-manager -f però tampoc. No sé què faré perquè no sé quan m'hi podré tornar a dedicar una bona estona. Aniré informant.

Gràcies de tota manera, com sempre.

---

