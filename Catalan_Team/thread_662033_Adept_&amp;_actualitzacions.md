---
title: "Adept &amp; actualitzacions"
date: 2008-01-08
forum: Catalan Team
---

### Post by farigola on 2008-01-08
Hola,
No tinc idea de que ha passat, però no puc actualitzar l'equip, cada cop que intento actualitzar el contingut surt el missatge:
S'ha produït un error en aplicar els canvis. Probablement hi ha hagut un problema descarregant alguns paquets o l'aplicació trencaria paquets.
He vist que aquest error està.
Després de diferents consultes he fet l'execució de sudo apt-get -f install, però tot continua igual.

He de mirar més referències, però ara pera no tinc idea de com seguir aquest tema. Teniu alguna pista?
Gràcies

---

### Post by papapep on 2008-01-08
Enganxans el contingut del teu /etc/apt/sources.list, si us plau.

---

### Post by farigola on 2008-01-08
Hola
Gràcies per contestar. Aquí teniu el contingut del fitxer.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-security main restricted
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-security universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) gutsy-security multiverse
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

---

### Post by papapep on 2008-01-08
I quan fas el sudo apt-get install -f què et surt al terminal?

---

### Post by farigola on 2008-01-08
Gràcies per les teves indicacions. He vist que hi ha un paquet en mal estat, ja havia vist aquest missatge, però no m'hauria imaginat que això fos la causa del problema, penso.

jordi@ordinador:~$ sudo apt-get -f install
[sudo] password for jordi:
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
E: El paquet dcp330ccupswrapper necessita ser reinstal·lat, però no se li pot tr                                     obar un arxiu.
jordi@ordinador:~$

Després d'aquest missatge he fet una execució del programa aptitude per intentar eliminar el paquet, amb el resultat del següent: 

S'estan preconfigurant els paquets...
dpkg: s'ha produït un error en processar dcp330ccupswrapper (--remove):
 El paquet està en un estat molt dolent e inconsistent - el tindreu que
 reinstal·lar abans d'intentar desinstal·lar-lo.
S'han trobat errors en processar:
 dcp330ccupswrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
S'ha produït un error en la instal·lació del paquet. S'està intentant restablir.
Premeu retorn per continuar.

Sota la meva ignorància, El fet que un paquet estigui malament ha de ser causa de que no funcioni Adept?

---

### Post by papapep on 2008-01-08
Adept, Synaptic, Aptitude, apt-get i tots plegats són només interfícies per a gestionar la base de paquets amb dpkg. Arribats aquí, si un paquet està en un estat no-correcte (per dir-ho d'alguna manera), provoca que tota la base també estigui en un estat no-correcte, fet pel qual fins que no es solucioni el problema amb el paquet qualsevol altra actuació seria embolicar la troca.
Així, el sistema de gestió com que és molt intel·ligent, es "para en sec" fins que no detecti que no hi ha problemes.

Aleshores, tal i com et diu l'error, cal que tornis a reinstal·lar el paquet aquest que et diu (dcp330ccupswrapper), que suposo que el deus haver instal·lat manualment donat que no és als repositoris oficials. 
Un cop ho hagis fet, el apt-get install -f t'hauria de funcionar i la resta d'operacions amb paquets també.

---

### Post by farigola on 2008-01-09
Alguna cosa rara vaig fer que ara no hi ha manera de fer servir la impressora. He  intentat tornar a insta·lar el driver, però he vist que diferents directoris havien desaparegut, he tornat a crear-los, però no aconsegueixo recuperar el driver, però si el programa d'actualitzacions Adept, doncs ja funciona.
Ara he de recuperar la impressora.

---

