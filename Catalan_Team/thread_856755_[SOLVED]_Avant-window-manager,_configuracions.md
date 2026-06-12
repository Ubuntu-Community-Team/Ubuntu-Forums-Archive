---
title: "[SOLVED] Avant-window-manager, configuracions"
date: 2008-07-11
forum: Catalan Team
---

### Post by Druiling on 2008-07-11
Bones a tothom.
Aquest post neix de la necessitat, manifestada pel company Sisco de no crear confusió, per tant, al tema, que té tota la raó.

Vaig demanar com crear els applets al awn manager perquè no veia la manera. El company Jaume 69 em va respondre això:

> **jaume69 said:**
> -Arrossegant les icones fins la barra **AWN **les pots afegir.

-Deus haver instal.lat la versió **Hardy** i no la de **Launchpad**.

Si vols pots desinstal.lar la que tens i instal.lar la de **Launchpad**.

A mi em funciona bé.

sudo gedit /etc/apt/sources.list

```
    deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
    deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main


```

sudo apt-get update

sudo apt-get install awn-manager-trunk awn-extras-applets-trunk

:lolflag:

Seguint aquests passos però, en trec això que segueix:

maria@maria-laptop:~$ deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
bash: deb: command not found
maria@maria-laptop:~$ deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
bash: deb-src: command not found
maria@maria-laptop:~$ 

No sé què no veig...

Salut!!!:biggrin:

---

### Post by jaume69 on 2008-07-12
Tens que posar al Terminal:

**sudo gedit /etc/apt/sources.list**

I afegir els repositoris de Launchpad.

```
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

```
Per últim,al Terminal:

[B]sudo apt-get update

sudo apt-get install awn-manager-trunk awn-extras-applets-trunk
[/B]
-_________________-

Si et falta algun paquet ho pots mirar al Synaptic.

---

### Post by Druiling on 2008-07-12
Fet!!!
Moltes gràcies.
Salut.:lolflag:

---

### Post by FloiT on 2008-07-16
disculpeu que reobri una línia ja SOLVED, però estic interessat en instal·lar la versió AWN de launchpad però sóc molt novell, i m'agradaria que algú precisés on haig d'afegir akell parell de línies de codi 

[INDENT]deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
    deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main[/INDENT] 

dins del sources.list. És indiferent?

Gràcies

---

### Post by oriolsbd on 2008-07-16
En principi, és el mateix. Una altra cosa és si vols tenir el sources.list una mica ordenat, i tenir els repositoris oficials al principi i els que afegeixes manualment al final. :-)

Salut!

---

### Post by FloiT on 2008-07-16
ok, thanks!

---

### Post by Druiling on 2008-07-17
Hola, 
Jo tampoc no ho veia clar, però segueix el que diu en Jaume69.
Quan facis això:

> **jaume69 said:**
> Tens que posar al Terminal:

**sudo gedit /etc/apt/sources.list**

Se t'obrirà una finestra, al final de tota la parrafada que et surt, pica això:

I afegir els repositoris de Launchpad.

```
deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) hardy main

```

Desa-ho i segueix amb això:

Per últim,al Terminal:

[B]sudo apt-get update

sudo apt-get install awn-manager-trunk awn-extras-applets-trunk
[/B]
-_________________-

Si et falta algun paquet ho pots mirar al Synaptic.

A mi em va funcionar perfectament.

Salut!!

PD: si he fet algun pas malament, agrairé que ho corregiu!

---

