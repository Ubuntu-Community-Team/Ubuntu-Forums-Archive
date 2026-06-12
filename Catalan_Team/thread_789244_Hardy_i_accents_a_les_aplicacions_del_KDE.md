---
title: "Hardy i accents a les aplicacions del KDE"
date: 2008-05-10
forum: Catalan Team
---

### Post by Bensy on 2008-05-10
Tinc el clàssic problema amb les aplicacions del KDE en que les vocals amb agut apareixen com a vocals sense res, i amb greu amb l'accent abans, en comptes de damunt.

He estat hores buscant al google i per ací, i cap de les solucions m'han servit al Hardy.

Algú ha pogut sol·lucionar-ho? També m'apareixen els menús mig en català, mig en anglès, i he vist que és per culpa de tindre els locales amb ca_ES.UTF-8@valencia, però no puc canviar-ho.

Si faig sudo gedit /etc/environment tinc:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="ca_ES:ca:en_GB:en"
LANG="ca_ES.UTF-8"

Però si faig locale:

LANG=ca_ES.UTF-8@valencia
LC_CTYPE="ca_ES.UTF-8@valencia"
LC_NUMERIC="ca_ES.UTF-8@valencia"
LC_TIME="ca_ES.UTF-8@valencia"
LC_COLLATE="ca_ES.UTF-8@valencia"
LC_MONETARY="ca_ES.UTF-8@valencia"
LC_MESSAGES="ca_ES.UTF-8@valencia"
LC_PAPER="ca_ES.UTF-8@valencia"
LC_NAME="ca_ES.UTF-8@valencia"
LC_ADDRESS="ca_ES.UTF-8@valencia"
LC_TELEPHONE="ca_ES.UTF-8@valencia"
LC_MEASUREMENT="ca_ES.UTF-8@valencia"
LC_IDENTIFICATION="ca_ES.UTF-8@valencia"
LC_ALL=

Supose que he de canviar açò, però no he trobat com.

Moltes gràcies.

---

### Post by CarlesOriol on 2008-05-11
Comprova al kcontrol la llengua que tens seleccionada.

Uses gnome i aplicacions en kde o tot en kde?

Dius que tens el clàssic problema... això vol dir que ja t'havia passat abans? Que coneixes a algú més que li passi?

---

### Post by Bensy on 2008-05-12
He anat a obrir el kcontrol, i no el tinc instal·lat. L'acabe de posar a instal·lar ara.

Faig servir Gnome (Ubuntu vulgaris) amb aplicacions del KDE.

Aquest problema ja el vaig tindre una de les vegades que vaig instal·lar Gutsy, i buscant al google vaig trobar moltíssima gent que comentava el mateix problema. Pots comprovar-ho fent "KDE no accents" al google. El cas es que ni m'en recorde de com ho vaig solucionar l'altra vegada ni res, i ja he provat tot el que se m'acudeix.

Per cert, els menús ja els tinc completament en català, però no sabria dir quina de totes les coses que vaig fer va solucionar això. Ara miraré al kcontrol.

He canviat al kcontrol la codificació a UTF-8 i la llengua al català. De moment no fa res, però vaig a reiniciar per estar-ne segur.

EDITAT: En reiniciar va igual. Supose que he de llevar la part que diu "@valencia" del que m'ix quan faig locale, el cas és que no sé en quin fitxer hi és, això.

---

### Post by CarlesOriol on 2008-05-12
Bé. Insta&#320;la el kde usant el paquet kubuntu-desktop inicies un cop en kde i quan tornis a engegar els programes en gnome ja et funcionarà correctament tot.

---

### Post by Bensy on 2008-05-13
He instal·lat el KDE. Quan carrega apareix el logo de Kubuntu, però a partir de la pantalla de registrar-se, està tot com ho tenia adès, inclòs el problema dels accents, però amb tot el programari per defecte de Kubuntu al menú d'aplicacions. Com ho faig per a iniciar amb el KDE? I per a canviar després al GNOME? Quan ho tinga sol·lucionat, podré desinstal·lar el KDE sense que em pete res?

---

### Post by lluisanunez on 2008-05-13
A la mateixa pantalla de login, clica a baix a l'esquerra "Accions" (crec) i allà pots triar la sessió, que et deixarà triar entre Gnome, KDE o el que tinguis instal.lat
Per al tema dels accents, has entrat a Sistema > Administració > Suport idioma?

---

### Post by Bensy on 2008-05-13
Des de la finestra de login he canviat Català@valencia a Català vulgaris, i ho he fet predeterminat per al KDE i per al GNOME. La única millora és que ara sí apareixen els aguts, però també davant de la vocal. Al KDE em fa el mateix que al GNOME, a les seues aplicacions no funcionen els accents correctament, però a d'altres com el Writer sí piulen.

---

### Post by orestesmas on 2008-05-13
A veure, això no pot ser. Alguna cosa devem estar fent malament...

Pots obrir un terminal en mode gràfic (konsole o similar) i posar:

```

env | grep LANG

```

a veure què surt?

P.D. Que el writer vagi bé és normal, perquè és una aplicació autocontinguda que "passa" de la configuració de l'escriptori, ja sigui gnome, o kde.

---

### Post by Bensy on 2008-05-14
bensy@lacabaretera:~$ env | grep LANG
LANG=ca_ES.UTF-8
GDM_LANG=ca_ES.UTF-8

També puc fer servir accents al gedit o quan canvie el nom d'un arxiu, això si és del GNOME, no? Ara al Firefox, també van bé.

---

### Post by eselma on 2008-05-15
Sembla que el *locale* que instal·la[COLOR="Blue"] kubuntu 8.04[/COLOR] per omissió (ca_ES.UTF-8@valencia) realment té el mateix nyap (o semblant) que el ca_AD. Jo també m'hi vaig trobar i es va arreglar a tot arreu un cop vaig editar el fitxer */etc/default/locale* deixant-lo només amb ca_ES.UTF-8, com abans.

Algú més s'hi ha trobat?

---

### Post by orestesmas on 2008-05-15
Sembla que la variable LANG és correcta... pots copiar aquí el contingut del fitxer /var/lib/locales/supported.d/ca ?

---

### Post by Bensy on 2008-05-16
ca_AD.UTF-8 UTF-8
ca_ES.UTF-8 UTF-8
ca_ES.UTF-8@valencia UTF-8
ca_IT.UTF-8 UTF-8
ca_FR.UTF-8 UTF-8

Açò he trobat. Encara en queda un @valencia, però he preferit esperar consell abans d'esborrar-ho. Pareix que tinc el català dues vegades amb ambdues variants instal·lades? Què és exactament aquest fitxer? Així a banda de solucionar el problema, aprenc una miqueta. :)

Una altra vegada, gràcies per l'interès.

---

### Post by algc80 on 2008-10-03
Hola a tots..

Aquest tema està resolt en algun lloc?

Em passa el mateix en 2 instal·lacions de Hardy, afectant a l'aMsn y a l'Skype.

Salut,

---

### Post by CarlesOriol on 2008-10-04
Has comprovat el que deia al fil: instalar el paquet kubuntu-desktop??

---

### Post by trinkus on 2008-10-04
Ep!

A mi em passava el mateix!
Només va marxar traient qualsevol locale amb català d'Andorra ca_AD
Es veu que hem de ser espanyols i el d'Andorra té un bug
Consistia en treure el locale _Ad pero no recordo com es fa per treure-ho, pero vaja, que us he de quedar amb el ca_ES

---

### Post by orestesmas on 2008-10-04
Em sembla que el problema és al fitxer /etc/default/locale. Per tal que funcionin els accents hauria de tenir
```

LANG="ca_ES.UTF-8"

```

Prova-ho a veure què tal (hauràs de recarregar la configuració del sistema. La menera simple de fer-ho és reiniciar)

---

