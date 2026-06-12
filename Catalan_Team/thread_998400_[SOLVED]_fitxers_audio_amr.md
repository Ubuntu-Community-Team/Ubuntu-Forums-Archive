---
title: "[SOLVED] fitxers audio amr"
date: 2008-11-30
forum: Catalan Team
---

### Post by jinglada on 2008-11-30
Hola, el mplayer diu: cannot find codec for audio format 0x726D6173, el Totem diu: Hauríeu d'instal·lar el connector Adaptive Multi Rate NarrowBand (AMR-NB) decoder per a reproduir aquesta pel·lícula i el Rythmbox diu: No s'han trobat els connectors del GStreamer per a descodificar fitxers «tipus audio/x-amr-nb-sh».

Què em recomaneu?

---

### Post by LitusMayol on 2008-11-30
[RealPlayer]("http://spain.real.com/player/select/") versió per a GNU/Linux reprodueix *.amr*. Fins ara per a mi ha sigut la solució.

---

### Post by jinglada on 2008-12-01
M'he descarregat el RealPlayer11GOLD.bin però no sé com s'instal·la. Em podeu indicar com fer-ho o algun fil on s'explica?

---

### Post by oriolsbd on 2008-12-01
El RealPlayer està al repositori de Medibuntu. Si l'afegeixes als teus repositoris, podràs instal·lar-lo des de Synaptic. Per a fer-ho edita el fitxer /etc/apt/sources.list:

```
sudo gedit /etc/apt/sources.list
```

Afegeix aquesta línia (millor al final):

```
deb http://packages.medibuntu.org/ intrepid free non-free
```

Nota: Si tens instal·lat Ubuntu 8.04, has de posar "hardy" en comptes d'"intrepid".

Un cop modificat el fitxer, has de fer que el sistema agafi els nous paquets:
```
sudo apt-get update
```

Un cop ja tens ben configurat el repositori de Medibuntu, primer has dinstal·lar-te el paquet "medibuntu-keyring", que conté la clau d'encriptació dels paquets de Medibuntu. Ho pots fer des de Synaptic.

Quan ja tinguis instal·lat aquest paquet, ja podràs instal·lar-te el RealPlayer (el paquet es diu "realplayer"), o qualsevol altre programa de Medibuntu (ho pots fer des del Synaptic, per exemple). Pots mirar tots els que hi ha [aquí]("http://packages.medibuntu.org/intrepid/index.html").

Salut!

---

### Post by jinglada on 2008-12-01
Gràcies Oriol. Mira que em passa:
> **oriolsbd said:**
> ```
sudo apt-get update
``` al final em dona un error: 
...
46,9kB descarregats en 4s (11,5kB/s)                              
S'està llegint la llista de paquets... Fet
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: Les següents signatures no s'han pogut verificar perquè la clau pública no està disponible: NO_PUBKEY 2EBC26B60C5A2783
W: Potser voldreu executar apt-get update per a corregir aquests problemes
joan@joan-laptop:~$ 

Què he de fer?

> "medibuntu-keyring"

Al synaptic hi tinc l'ubuntu-keyring. És el mateix?

---

### Post by oriolsbd on 2008-12-01
Ja és correcte que et dóni l'error de GPG fins que no instal·lis el "medibuntu-keyring". Aquest paquet no és el mateix que el "ubuntu-keyring". Pots comprovar (a través del filtre de Synaptic) que no el tinguis? Em sembla recordar de quan ho vaig fer jo que em donava aquest error i primer no veia el paquet, però en tornar a entrar a Synaptic ja hi era.

Una manera senzilla de buscar-ho a través de Synaptic és seleccionant el botó de mà esquerra avall, on posa "Origen". Ara podràs buscar específicament en cadascun dels repositoris que tens. Vas al que posa "packages.medibuntu.org/free" i t'haurien de sortir diversos paquets (uns 10), entre ells el "medibuntu-keyring".

En els repositoris de Medibuntu veuràs que hi ha altres programes que et poden resultar interessants (o no, perquè la majoria d'ells tenen alternatives ja instal·lades): Skype, Acrobat Reader, Google Earth, i altres.

---

### Post by oriolsbd on 2008-12-01
Per cert, en els repositoris de Medibuntu hi ha dos paquets ("amrnb" i "amrwb") que suposo que deuen ser els códecs d'amr que estàs buscant. Jo no els tinc instal·lats, però per la descripció sembla que ho siguin.

Salut!

---

### Post by jinglada on 2008-12-01
Gràcies Oriol,
tot instal·lat i funcionant. A part del realplayer ho he pogut sentir en el mplayer. En canvi segueix sense funcionar en el Totem i en el Rythmbox, amb els mateixos missatges que dono en el post inicial del fil.

---

