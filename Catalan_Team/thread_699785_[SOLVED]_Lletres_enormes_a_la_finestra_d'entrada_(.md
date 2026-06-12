---
title: "[SOLVED] Lletres enormes a la finestra d'entrada (gdm)"
date: 2008-02-17
forum: Catalan Team
---

### Post by lpargemi on 2008-02-17
Hola

He instal.lat a un portàtil una partició amb Ubuntu 7.10, treta de l'enllaç d'aquesta pàgina. 

Tot va bé, però a la finestra d'entrada per arrencar, la mida dels fonts és tan gran que no hi ha manera de saber quin usuari estàs escrivint. Sabeu on es pot canviar, perquè a l'apartat de configuració de la finestra d'entrada no ho he sabut veure.

Sort que mestressa es diu Eva, i l'usuari per tant és molt curt. Queda lleig que la primera cosa fa una nova ubuntaire ja hagi de començar-la amb nyaps (imaginant-se que ha escrit bé el nom)...

Salut

Lluís

---

### Post by papapep on 2008-02-17
Hi ha bastants casos com aquest que dius, i molts,sembla, que tenen a veure amb la configuració de la targeta gràfica. Quina gràfica i quin controlador fa servir el portàtil aquest que dius?

---

### Post by CarlesOriol on 2008-02-18
Una intel segurament oi.

**Ves a Sistema** > **Administració** > **Finestra d'entrada** > 

**Seguretat **> **Configura servidor X** > 

i canvies 

**/usr/bin/X -br -audit 0  **

per 
[B]
/usr/bin/X -br -dpi 96  -audit 0[/B]

(ah... i reinicia el gdm)

---

### Post by lpargemi on 2008-02-18
Hola

El vídeo és una intel 945, la que vé a un HP Compaq nx 7300

El controlador instal.lat és intel - Experimental modesetting for intel integra..., em sembla que de 3dlabs , oxygen gmx.

De qualsevol manera amb les instruccions d'en Carles Oriol ha funcionat bé

Agraït

Lluís

---

### Post by Druiling on 2008-02-24
No sé si està bé posar una pregunta en un fil resolt, però la poso i em dieu si si o si no, d'acord?.
Jo tinc el mateix problema de les lletres enormes, he mirat la tarja gràfica i la veritat no entenc què haig de fer, perquè tinc una cosa per defecte (captura1), i tinc unes quantes opcions si trio el model del portàtil (captura2). Puc començar a enredar en les opcions, però temo posar-ne una molt inadequada i que no em permeti veure com engegar si em carrego quelcom.
Em podeu orientar, si us plau?
Gràcies.

---

### Post by papapep on 2008-02-24
La targeta gràfica no la toquis que crec que la tens bé (de fet l'únic que et falla és el tema de l'entrada gràfica i la mida de la font, no?).

El que hauries de provar és el que ha dit en Carles tres posts més amunt. Si no tens clar com fer-ho, pregunta què no entens en concret.

---

### Post by Druiling on 2008-02-25
Bé, he fet això que diu en Carles. Ara bé, no veig cap opció per a reiniciar el gdm. El que he fet es tancar i tornar a obrir i reiniciar l'ordinador però estic igual.
Què faig malament?

---

### Post by lpargemi on 2008-02-25
Hola

Jo per rearrencar també vaig fer com tu: apagar la màquina i tornem-hi.

He mirat com va quedar la pantalla de configuració, i a la teva sembla que hi hagi un caràcter blanc després del darrer "zero"  que a la meva no hi és. Potser no hi tingui res a veure, o si...

Salut

Lluís

---

### Post by Druiling on 2008-02-25
M'ho miro.
Gràcies Lluís.

---

### Post by Druiling on 2008-02-25
Doncs no. He tret l'espai i seguim igual.
En fi...

---

