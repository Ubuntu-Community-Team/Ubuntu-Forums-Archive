---
title: "Com gravar un disc de música en un iso"
date: 2008-07-30
forum: Catalan Team
---

### Post by xoldy on 2008-07-30
Hola a tots, bon dia, voldria saber si algú de vosaltres sap com gravar un disc de música en una iso enlloc d'utilitzar un disc físic.
Normalment faig servir aquesta opció per muntar la iso, i obtindre els noms de les cançons per poder convertir el disc a mp3 o ogg. Amb el Nero es podia seleccionar si volies fer la gravació a la unitat dvdr o bé en una iso. Normalment amb el Linux estic utilitzant el k3b, però no se veure l'opció.

Moltes gràcies a tots.

---

### Post by papapep on 2008-07-30
[mkisofs]("http://packages.ubuntu.com/hardy/mkisofs") et farà la feina. Pàgina MAN: [http://linux.die.net/man/8/mkisofs](http://linux.die.net/man/8/mkisofs)

---

### Post by oriolsbd on 2008-07-30
A Hardy es va substituir el paquet mkisofs pel genisoimage. Ho dic perquè el mkisofs no el trobaràs pel Synaptic (excepte si l'han tornat a posar les últimes setmanes).

Seguint els enllaços del Papapep, pots trobar la pàgina MAN: [http://linux.die.net/man/1/genisoimage](http://linux.die.net/man/1/genisoimage)

Salut!

---

### Post by carlesdalmases on 2008-07-31
Tot torna en aquesta vida...

Heu respòs una pregunta que vaig fer jo mateix fa uns mesos, i que sembla que vaig arribar a unes conclusions equivocades !

[http://ubuntuforums.org/showthread.php?t=735461&highlight=carlesdalmases](http://ubuntuforums.org/showthread.php?t=735461&highlight=carlesdalmases)


Gràcies

---

### Post by orestesmas on 2008-07-31
> **xoldy said:**
> Hola a tots, bon dia, voldria saber si algú de vosaltres sap com gravar un disc de música en una iso enlloc d'utilitzar un disc físic.


No cal que usis mkisofs ni cap altre programa de terminal, que per fer ISOS la quantitat d'opcions i punyetes és gran.

Simplement ves al K3B, crea un nou projecte de CD d'àudio, arrossega-hi els fitxers a gravar, digues-li "grava" i aleshores aquí és on has de marcar la caixa de selecció que diu "crea la imatge i prou". Llavors només crearà la ISO sense gravar-la al CD.

---

### Post by xoldy on 2008-08-04
Moltes gràcies a tots. Provaré totes les solucions, encara que d'entrada em cridi més l'opció del k3b perquè sembla més directe. De tota manera veig que hi ha programes que per comandes són molt potents perquè dóna moltes opcions.

Com sempre gràcies a tots.

---

