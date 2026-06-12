---
title: "Simulador de circuits pneumàtics (tipus FluidSIM)"
date: 2008-09-29
forum: Catalan Team
---

### Post by RainCT on 2008-09-29
Bones,

Sabeu si hi algun programa per a GNU/Linux semblant al [FluidSIM](http://www.fluidsim.de/fluidsim/index4_e.htm)?

---

### Post by orestesmas on 2008-09-30
Programari lliure tan específic no en conec cap, però segons el que vulguis fer pots utilitzar un programari científic de propòsit més general. Jo normalment faig servir Octave (per sistemes lineals) o Scilab/Scicos (per sistemes no lineals). Casualment, mentre em repassava [el web]("http://www-rocq.inria.fr/scicos/") d'aquests darrers per veure si tenia alguna "toolbox" d'hidràulica/pneumàtica, he vist que justament hi ha una nova extensió per aquest tipus de sistemes:

> 
 Scicos is used for signal processing, systems control, queuing systems, and to study physical and biological systems. New extensions allow generation of component based modeling of electrical and hydraulic circuits using  the Modelica language.


A més veig que fa servir el llenguatge "[Modelica]("http://www.modelica.org/")" (que jo no coneixia), i que justament serveix per simular sistemes físics complexos, inclosos els hidràulics (parlo tota l'estona d'hidràulica perquè és el que surt, però suposo que la pneumàtica també hi deu ser inclosa).

Mira-t'ho i tu mateix veuràs si et serveix o no.

---

### Post by RainCT on 2008-10-05
Ah, sembla que aquests són més complicats...

Preguntava perquè estem fent servir el FluidSIM a l'institut i com que els d'informàtica estan pensant en la possibilitat de passar a GNU/Linux volia saber si hi ha alguna alternativa que hi funcioni.

Bé, gràcies per la informació :).

---

