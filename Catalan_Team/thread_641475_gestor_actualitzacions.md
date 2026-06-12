---
title: "gestor actualitzacions"
date: 2007-12-15
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2007-12-15
Hola a tots.
Al Gestor d'Actualitzacions no hem surt l'opció d'actulitzar  a 7.10
Ara tinc Ubuntu 7.04
Donat que amb modo gràfic no ho puc fer, algú sap com actualitzar
des de  consola?
disposo del cd 7.10
Moltes gracies.

---

### Post by SiscoGarcia on 2007-12-15
Abans de res, hauries de tenir actualitzat el 7.04 i llavors et sortiria l'opció d'actualitzar-te a la versió 7.10. Al menys és el que em va passar a mi.

---

### Post by CarlesOriol on 2007-12-16
Tens conexió a internet?

---

### Post by Miquel Ubuntero on 2007-12-16
Sí tinc ADSL i si estic actualitzat.
Alguna pregunta més?
gracies ;)

---

### Post by Miquel Ubuntero on 2007-12-18
Hola.
He provat el següent des de consola:
miquel@miquel-desktop:~$ sudo update-manager
warning: could not initiate dbus
miquel@miquel-desktop:~$ 

Sembla que falla el dbus
que no se que es ni com sol·lucionar-ho

Cap idea?
Gracies.

---

### Post by papapep on 2007-12-18
Prova ficant una -p al final de la ordre:

```
sudo update-manager -p
```

---

### Post by Miquel Ubuntero on 2007-12-19
He provat el que Papapep diu però no va:

miquel@miquel-desktop:~$ sudo update-manager -p
Password:
warning: could not initiate dbus
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

gracies pel teu interès.

P.D.: la ADSL tira be.

---

### Post by papapep on 2007-12-19
Quina versió de update-manager tens?

```
sudo apt-cache show update-manager
```

Si tens la 0.59.20 és la correcta.

En tot cas, també pots provar a actualitzar a la manera que es feia fins fa no massa (tot i que hi ha gent que diu que no és la manera correcte ara, i que pot tenir efectes colaterals):

[COLOR="Red"]**NOTA IMPORTANT 1**[/COLOR]: Aquest és el mètode d'actualització que jo, i molta altra gent, he fet servir sempre, i no he tingut mai cap gran problema amb ell, però NO puc assegurar que li vagi bé a tothom. Per tant, si ho feu, ho feu pel vostre compte, i assumint vosaltres el, suposat, risc.
[B][COLOR="Red"]
NOTA IMPORTANT 2 [/COLOR][/B]: Si tens una placa de video "complicada" és molt probable que en pujar de versió, s'hagi de configurar tot de nou. El qual pot ser fàcil o difícil, depenent del model. Ho dic per a que ho tingueu present.

Pas 1. Assegurar que tens la Feisty a "l'últim crit":

```
sudo aptitude update
```

i després

```
sudo aptitude safe-upgrade
```

Pas 2. Canviar totes les referències dins el fitxer /etc/apt/sources.list de Feisty a Gutsy:

```
sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list
```

Un altre cop, sincronitzem la base de paquets amb el repositori:

```
sudo apt-get update
```

Pas 3. Executem la actualització pròpiament dita:


```
sudo apt-get upgrade
```

Un cop fet això, i comptant que tot hagi anat bé, reiniciem el sistema i ja hauriem de tenir un Gutsy Gibbon (7.10) funcionant.

---

### Post by idrojsnop on 2007-12-23
jo tinc el mateix problema que ell, i Papapep, al dir-me que la versiò correcte de update-manager és 0.59.20, doncs em fa l'afecte que jo no la tinc pas aqeusta. Tot i que tinc l'Ubuntu tal i com venia a la Iso del CD. Us passo el que m'ha sortit a la terminal:

idrojsnop@snoopy:~$ sudo apt-cache show update-manager
Package: update-manager
Status: install ok installed
Priority: optional
Section: gnome
Installed-Size: 2144
Maintainer: Michael Vogt <michael.vogt@ubuntu.com>
Architecture: all
Version: 1:0.81
Depends: python2.5, python-central (>= 0.5.8), python (<< 2.6), python (>= 2.4), gconf2 (>= 2.10.1-2), update-manager-core (= 1:0.81), python-glade2, synaptic (>= 0.57.8), gksu, python-dbus, python-vte, python-gconf
Description: GNOME application that manages apt updates
 This is the GNOME apt update manager. It checks for updates and lets the user
 choose which to install.
Python-Version: 2.4, 2.5

Gràcies.

---

### Post by papapep on 2007-12-23
La 0.59.20 és la versió més actual per a la Feisty. Amb quina versió de Ubuntu estàs??

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=update-manager&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=update-manager&searchon=names&subword=1&version=all&release=all)

Fes:

```
uname -a
```

```
cat /etc/apt/sources.list
```

i enganxa'ns el resultat.

Per cert, quan enganxeu missatges del sistema heu de fer servir l'etiqueta "CODE" (els dos "iguals" creuats), per que si no passa el que t'ha passat, que el fòrum converteix certes combinacions de caràcters en emoticones i perdem informació

---

### Post by idrojsnop on 2007-12-23
Bé, aqui ho tens. Gràcies per l'interès.

```
idrojsnop@snoopy:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://es.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://es.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://es.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://es.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://es.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://es.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://es.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://es.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://www.getautomatix.com/apt gutsy main

```

---

### Post by papapep on 2007-12-23
Quin poti-poti de fitxer... :-)

Edita'l amb la ordre:

```
sudo nano /etc/apt/sources.list
```

Hauria de quedar així:

```

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

deb http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe

```

Surt desant amb Ctrl+X.

Respecte la última línia del teu fitxer sources.list, que és el repositori de l'automàtix, doncs què dir més....que no el feu servir, que només fa que destrosses.

Un cop hagis modificat el fitxer fes:

```
sudo aptitude update
```

I un cop estigui:

```
sudo aptitude safe-upgrade
```

---

### Post by idrojsnop on 2007-12-24
Bé, ara tinc un petit problema. M'he instal·lat la versió que tu recomenaves del "update-manager-core", la 0.59.20, però ara no em deixa instal·lar els seus altres dos components. l'update manager, i l'update-notifier. 

Acavo de fer tot lo del codi anterior, explica'm pq ho he hagut de fer, sisplau. Pq sempre em trobo amb el mateix problema, faig coses, però no sé que faig, i aixina no hi ha manera de que aprengui, hehe:).

Moltes gràcies.

---

### Post by idrojsnop on 2007-12-24
Em diu que: ```

Package update-manager has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and
 never uploaded, has been obsoleted or is not available with the contents 
of sources.list

```

Per tant suposo que haig d'afegir alguna línia al sources.list. Oi?

---

### Post by CarlesOriol on 2007-12-24
Més aviat sembla que has insta&#320;lat un paquet deb d'una font diversa i a l'hora d'actualitzar les dependencies (llibreries o requeriments) per fer-lo funcionar s'actualitzaran deixan-te el programa coix de llibreries i per tant bloquejant-te la operació

---

### Post by Miquel Ubuntero on 2007-12-30
Hola de nou.
He reprès el tema intentant actualitzar tal com va recomenar en papapep. Però no a quedat actualitzat. si que he tingut alguns canvis inesperats. Idioma canviat i alguna coseta més. Però no importa. Es el pc de casa i no hi ha res sense una bona copia de seguretat.
Ara penso tirar pel dret i formatar el H.D.
Tinc una pregunta, si us plau.
Si faig una copia de seguretat del tot el "home", o be d'un usuari, per ex. "Home/miquel". Puc després d'instal·lar Ubuntu 7.10 amb aquesta copia recuperar tots el docs de la carpeta "LLocs", config correo, etc?
Moltes gracies de nou a qui s'interesi pel tema.
Salut! i bon any!

---

### Post by CarlesOriol on 2007-12-30
Si.
Assegurat que es copiïn tots els arxius ocults.

Jo uso per fer les copies a un hdd temporal:

```
rsync -urvt --delete --delete-excluded --exclude="carles/.googleearth/*" --exclude "carles/descarregues/*" --exclude="carles/.thumbnails/*" --exclude="carles/.Trash/*"  --exclude="carles/.cache/*" --exclude="carles/.beagle/*" /home/carles /media/copiadisc
```

Per si et pot servir de referència per les teves.

---

### Post by papapep on 2007-12-30
I si el que has de copiar és tota una partició cap a una altra partició, amb un simple:

```
dd if=/partició_origen of=/partició_destí
```

Fas un clon de la partició orígen bit a bit. Amb això fas una instantània de la partició i és una bona solució, per exemple, per si vols fer una imatge del sistema acabat d'instal·lar i conservar-la per d'altres ordinadors o pel mateix si tens "tendència" a reinstal·lar. 
No és, en canvi, una bona manera per a mantenir una còpia de seguretat d'un sistema en producció ja que cada cop fa una còpia sencera i no incremental, amb el consum de temps que això significa.

---

### Post by CarlesOriol on 2007-12-31
> **papapep said:**
> I si el que has de copiar és tota una partició cap a una altra partició, amb un simple:


O en aquest cas pots usar el partimage (tipus ghost) que sols copia l'espai del disc ocupat per dades i a més ens permet de comprimir-ho al mateix temps.

---

