---
title: "Petit problema amb gDesklets"
date: 2008-04-30
forum: Catalan Team
---

### Post by Frealof on 2008-04-30
Hola a tothom!

L'altre dia vaig estar remenant per internet tot buscant una manera de poder visualitzar la temperatura, velocitat dels ventiladors, etc. del meu pobre PC. Vaig trobar el gDesklets, el vaig instal·lar 

I molt feliçment vaig entrar a Applications/Accesòris per trobar que el gDesklet que vull utilitzar em diu que necessita no sé què d'un lm-sensors...

Busco per internet altre cop i aconsegueixo instalar-lo, activo els dispositius i posant "sensors" al terminal tinc un fantàstic registre de com estan les coses... 

Però continuo sense poder utilitzar el Desklet que en teoria em monitoritza la informació a l'escriptori (LMSensors with plotters ver 0.8), em surt la imatge d'un ventilador parat (quan no es així)...

A algú se li acud alguna cosa?

Salut!

---

### Post by Druiling on 2008-04-30
Hola, 
No sé si et servirà, però jo vaig trobar la solució a un problema semblant, desinstal.lant-los i tornant-los a instal.lar (des del synaptic).
Potser ho podries provar, a veure què.
Salut.

PD: De tota manera, i per si et pot fer servei, hi ha un post del juny 07, d'en bikerbaixcamp, que parla de les temperatures, igual pot fer-te servei fer-li un cop d'ull.

---

### Post by Frealof on 2008-04-30
Iep!

Doncs ho he provat i... no furul·la :(  Gràcies de totes maneres ;) He mirat el post al que feies referència i tampoc hi he trobat la solució...

Jo les temperatures, velocitat dels ventiladors, etc. posant la paraula *sensors* al terminal ja les hi veig, em surt tot llistat i bé. El problema es que el gDesklet aquest no sé perquè però no em funciona, bé, cap dels de la llista de LMSensors...

En fi, com deia als "palotes" sigue buscando... :)

---

### Post by niculau on 2008-05-02
No se per que no et funciona el gdesklet, però si poses en el terminal "sudo aptitude install sensors-applet" això et permetrà veure en la barra de tasques les temperatures, ventiladors, etc...

botó de la dreta/afegeix al quadre/hardware sensors monitor

salut

---

### Post by Frealof on 2008-05-04
Iep!

Perdoneu per contestar tard, he estat fent l'isard aquests dies i no he pogut contestar abans...

He provat el què comentaves, Nicolau, i funciona :) Gràcies!

Ara ja puc visualitzar a temps real com va tot... 

Tot i això encara no entenc què passa amb l'alpicació del gDesklets per monitoritzar totes aquestes dades del LMSensors :( Si algú vol/pot suggerir alguna coseta, serà benbinguda.

Salut!

---

### Post by niculau on 2008-05-04
suposo que hauràs de configurar alguna cosa en les propietats del desklet dient-li quin sensor tens en la placa base, etc...

---

### Post by Frealof on 2008-05-04
Iep!

Si, això seria el què s'ha de fer... 

Però quan clico el botó dret per obrir el diàleg on hi ha les diferents opcions, entre elles "configura el desklet",no m'hi apareix res...

De moment he instal·lat el que em vares proposar Nicolau i va de fàbula ;) però com que el fil el vaig obrir pel gDesklets, i com que de moment no ha aparegut "la solució" de moment el deixarem obert, si a ningú li sembla malament.

Per tant... seguirem amb el tema.

Salut!

---

