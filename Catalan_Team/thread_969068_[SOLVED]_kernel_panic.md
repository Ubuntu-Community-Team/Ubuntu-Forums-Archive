---
title: "[SOLVED] kernel panic"
date: 2008-11-03
forum: Catalan Team
---

### Post by bratac on 2008-11-03
Bones,

divendres vaig fer actualitzar un dels meus dos ordinadors amb ubuntu, vaig haver de marxar precipitadament de casa i vaig deixar l'actualització fent-se, fins avui no m'he tornat a mirar l'ordinador. Ja he trobat estrany que estés tancat, però no n'he fet cas i quan l'he engegat m'he trobat aquest missatge d'error:

[0.79211] kernel panic - not syncing: VFS unable to mount root fs on unknown-block (0,0)

Hi ha alguna manera de solucionar-ho?

gràcies!

---

### Post by torracastanyes on 2008-11-03
A mí també em passa, aproximadament dues de cada tres arrencades, però reiniciant-lo am el botó de la torre, al final, acaba arrencant (està instalat en un disc extern).

---

### Post by bratac on 2008-11-03
Gràcies torracastanyes, tanmateix m'agradaria poder trobar la solució al problema per tal d'evitar aquest missatge tant molest que en la majoria de casos no em deixa entrar al sistema.

He trobat explicacions del problema i solucions tanmateix no sé com puc aplicar-les, vull dir si ho he de fer sobre la pantalla que m'informa del kernel panic o si primer he d'entrar al sistema o com ho puc fer.

Gràcies per l'ajuda!

---

### Post by torracastanyes on 2008-11-03
Be, val a dir que no m'ho he mirat gaire perquè no és una instalació que em preocupi, vaig actualitzar-la per provar, avans d'actualitzar el sistema principal, i vist el resultat em sembla que m'esperaré una estona.

Sobre les solucions que has trobat, si pots passar un enllaç faría unes proves per veure com funciona, aviam si et puc ajudar.

---

### Post by torracastanyes on 2008-11-03
He aprofitat una estona per mirar d'on pot venir el problema, però estic igual. Aviam si el Mestres del fòrum ens poden donar alguna referència.

Pel que he trobat, el problema sol venir per dues raons:

1- El grub apunta a una partició errònia
2- El kernel no suporta el dispositiu

Entenc que en tots dos cassos es impossible que el sistema arrenqui sence cap correcció, per tant el problema ha de ser un altre, ja que a copia de reiniciar acaba arrencant.

Només se m'acut que pugui haber algun problema al carregar el driver que suporta el dispositiu (en el meu cas, un disc extern USB).

Algú sap per on puc començar a mirar?


Edito: Bratac, ens pots dir quin dispositiu tens i si has aconseguit arrencar-lo?

---

### Post by bratac on 2008-11-04
Tinc un ordinador d'escriptori amb una placa intel (no sé si 950) i el disc dur és intern. No puc accedir-hi ni reiniciant diverses vegades i pel que he llegit, crec que el problema rau en el que has dit tu, que el gurb apunta a un lloc on no toca. 

Ahir em vaig baixar el cd d'ubuntu, l'alternate i tot i que hi ha una opció d'arreglar sistemes espatllats el que proposava era un format (o almenys jo em vaig parar en aquest punt abans de perdre res) El que he pensat que faré serà baixar-me un cd normal instal·lar-ho de nou mantenint l'usuari i la configuració (i creuaré els dits per a que tot funcioni)

Tanmateix agrairia alguna altra solució que m'evités fer això. 

Gràcies.

---

### Post by torracastanyes on 2008-11-04
Si el problema es del grub, crec que es pot arreglar sence reinstalar, només arrencant amb un live i editant l'arxiu /boot/grub/menu.lst. El procediment l'he vist explicat als forums molts cops, però pel que veig, el format d'aquest arxiu ha canviat en aquesta versió i no goso posar-hi les mans.
A veure si algú ens pot dir com s'han fer els canvis per no ficar la pota.

---

### Post by bratac on 2008-11-04
Bones, cercant pels forums he trobat això: [http://ubuntuforums.org/showthread.php?t=27709](http://ubuntuforums.org/showthread.php?t=27709)

Les instruccions són les següents: 

> boot from live cd

mkdir /mnt/linux
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc

change source list into Breezy.

apt-get install initrd-tools
apt-get remove linux-image-2.6.10-5-686

it will remove 2.6.10 and install linux-image-2.6.12-2-686 .
Of course, I think it is still beta version..
but at least I can boot my system.

Però quan faig "mount -t proc /proc /proc" em diu: unable to resolve host ubuntu. Com ho he de fer per a que ho trobi? L'ordinador està connectat via ethernet a la xarxa tot i que sembla que no ara no funciona.

gràcies!

gràcies

---

### Post by quitus on 2008-11-04
proveu el supergrub, s'instal·la en un diskette i va de meravella.

salut

---

### Post by bratac on 2008-11-05
Gràcies Quitus! Aquesta nit ho provo.

De totes maneres, si no pogués recuperar el sistema voldria saber si copiant tota la carpeta home en un disc dur extern, fent una formatació del disc i instal·lant ubuntu de nou i després creant un usuari on hi posaria la carpeta home que tinc ara se'm mantindrien totes les configuracions (sobretot des de l'evolution i el Thunderbird)

gràcies!

---

### Post by bratac on 2008-11-06
Bones,
lo del super grub no m'ha funcionat (ara em dona un error anomenat 2) i a més a més he descobert que la tarja de xarxa tampoc va, dóna un error al libnss3 import/export. Crec que si puc solucionar això podré instal·lar ubuntu de nou. 

Em podeu ajudar i dir-me com solucionar-ho?

gràcies!

---

### Post by bratac on 2008-11-06
L'única solució que he trobat ha estat instal·lar el sistema de nou. Dono el fil per tancat. 

Torracastanyes, diga'm si vols que tanqui el fil o no.

fins ara

---

### Post by SiscoGarcia on 2008-11-06
> **bratac said:**
> L'única solució que he trobat ha estat instal·lar el sistema de nou. Dono el fil per tancat. 

Torracastanyes, diga'm si vols que tanqui el fil o no.

fins ara

A part que pots fer el que vulguis, evidentment, jo crec que NO hauries de tancar-lo perquè no has trobat una solució al teu problema, l'has "evadit", que és una altra cosa :-k

---

### Post by torracastanyes on 2008-11-06
Per la meva part, tampoc n'he tret l'entrallat, tot i que el meu problema no es tant greu de bon tros, només l'hi costa arrencar, pero després funciona.

---

