---
title: "Problema per a desactivar una tarjeta de so"
date: 2008-10-31
forum: Catalan Team
---

### Post by carles84 on 2008-10-31
HOla, sóc nou amb el Línux i tinc un xicotet problema amb el so, i és que tinc una placa base amb la tarjeta de so incorporada, però aquesta va fatal i per tant, me'n vaig comprar una, en Windows ho vaig solucionar inhabilitant la incorporada en la placa base però amb el línux no hi ha manera. He anat a la BIOS a "Perifèrics integrats" i he posat al PCI audio DISABLED, però continua detectant-me-la l'Ubuntu, i no sé que fer.

NO hi ha cap manera de dir-li que n'inactive una i aleshores funcione com si sols en tinguera una?

> root@Carles:~# asoundconf list
Please note that you are attempting to run asoundconf as a privileged superuser, which may have unintended consequences.

Names of available sound cards:
AudioPCI
CMI8738

Moltes Gràcies.

PD Si necessiteu cap altra dada, pregunteu i em dieu com aconseguir-la i ho faig en un bot.

---

### Post by francisc1701 on 2008-10-31
carles84, could you please translate this into English so that more people can understand?

---

### Post by papapep on 2008-10-31
Not in this forum, francisc1701. This is the Catalan speakers subforum :-)

---

### Post by francisc1701 on 2008-10-31
sorry:)

---

### Post by indiosincracia on 2008-11-01
quina placa base tens?
Pots triar el canvi de targeta des de Volume Control Preferences, o kmix?
Al manual "user guide" de la placa base trobaràs com desactivar el "Jumper" si no està soldat esclar.

---

### Post by carles84 on 2008-11-01
la placa base que té l'ordinador és la GA-7zmm de gigabyte.

---

### Post by papapep on 2008-11-01
Doncs a la pàgina 29 del [manual]("http://europe.giga-byte.com/FileList/Manual/motherboard_manual_ga-7zmm_e.pdf") [de la teva placa]("http://www.gigabyte.com.tw/Support/Motherboard/Manual_Model.aspx?ProductID=1367"), diu que modificant la posició del selector que marquen al croquis, es desactiva el dispositiu de so de la placa mare.

---

### Post by carles84 on 2008-11-02
ja ho he arreglat això, ara el problema el tinc que amb el 8.10 no conseguisc fer anar el so dels videos de youtube/etc quan amb el 8.04 si que podia.

---

### Post by papapep on 2008-11-02
Un tema = un fil :-)

---

### Post by indiosincracia on 2008-11-03
instal·la adobe flash 10 desde Synaptic

si no és això obra un altre fil (que és gratuït), :wink:

---

### Post by antoni2 on 2008-11-03
No se si et servira, pero jo em vaig trobar en un problema semblant per un altre cami: volia fer funcionar un DAC extern conectat per USB (conversor digital-analogic), que substitueix la placa de so de l'ordinador. Efectivament cal fer 

$ asoundconf list  (sense sudo)

--i suposem que et diu dos noms, la teva interna i la del DAC-USB:

PCM7209 
default

Llavors fas 

$ asoundconf set-default-card <nom-de-la-placa-que-vols-activar>

(en el meu cas era la 'default' sense cometes)

A mi em funciona consistent en Xubuntu 8.04 i 8.10.

[off-topic] Per cert, un DAC amb USB bé de preu i de molta qualitat es el de Musical Fidelity, model V-DAC. Uns 280 &#8364;. Les alternatives son molt més cares...

---

