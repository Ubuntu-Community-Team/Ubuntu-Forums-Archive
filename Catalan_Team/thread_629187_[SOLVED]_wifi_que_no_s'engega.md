---
title: "[SOLVED] wifi que no s'engega"
date: 2007-12-02
forum: Catalan Team
---

### Post by climent on 2007-12-02
hola,amics
El problema que tinc és que si apago i desendollo l'ordinador (portàtil Acer TravelMate 290), quan torno a engegar no s'activa el wi-fi. Això em passa tant si vaig amb bateria com en corrent, un cop desendollat l'ordinador la wifi s'ha acabat. Per defecte, sempre tinc en posició "on" l'interruptor de la wifi. Doncs si l'apago i desendollo, també sem queda morta la wifi. Sabeu si hi ha algun remei?

---

### Post by CarlesOriol on 2007-12-02
M'apunto a la pregunta. 

Tinc un Acer Aspire 5610 amb el mateix problema. Si no el desconnecto de la corrent al reiniciar l'ordinador tot funciona correctament però si el desconnecto cal que premi el pulsador per activar la xarxa.

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Però amb un altre acer similar (Aspire 5670) amb la mateixa placa de xarxa wifi això no passa.

De fet ja m'he acostumat a que quan moc el portàtil al engegar-lo activar manualment la xarxa... un rotllo!

---

### Post by papapep on 2007-12-02
I no has provat a veure si et funciona amb les acerhk?

---

### Post by CarlesOriol on 2007-12-02
Això és per les tecles especials... vaja... que res de res.

---

### Post by climent on 2007-12-02
Ja em pensava que hauria de connectar manualment, però el problema encara és més greu. Ni donant-li al polsador se'm posa en marxa. En el meu cas és un interruptor lliscant, i em sembla que ja he provat totes les opcions possibles: reiniciar l'ordinador i després lliscar l'interruptor, fer això primer i després engegar la màquina, etc. L'única manera que no falla és engegar primer en windows i un cop el wifi està engegat, reiniciar en ubuntu. No ho entenc. ARA QUE JA HAVIA TRET TOT EL WINDOWS!!!

---

### Post by papapep on 2007-12-02
Aquí asseguren que saben com arreglar-ho: [http://ubuntuforums.org/showthread.php?t=541953](http://ubuntuforums.org/showthread.php?t=541953)

---

### Post by jaume69 on 2007-12-02
Hola,suposo que el meu problema no se'n va gaire del fil..

Jo quan estic connectat a la meva xarxa wifi,després si faig ** iwlist scan** no funciona,només surt la xarxa a la que estic connectat.
En canvi si estic des-connectat si que em busca les xarxes wifi que hi ha al voltant.
¿?..

---

### Post by papapep on 2007-12-03
> Hola,suposo que el meu problema no se'n va gaire del fil..

Doncs això depen de que tinguis el mateix ordinador/dispositiu wifi, o no que els dos que plantegen la pregunta... :-)

---

### Post by jaume69 on 2007-12-03
> Doncs això depen de que tinguis el mateix ordinador/dispositiu wifi, o no que els dos que plantegen la pregunta...:) 

La wifi és la mateixa:
 description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:c2:f6:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=192.168.1.33 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g
__________________________
Abans, no tenia cap problema amb Feisty...
Gràcies.

---

### Post by CarlesOriol on 2007-12-06
> **jaume69 said:**
> 
1. Hola,suposo que el meu problema no se'n va gaire del fil..
2.Jo quan estic connectat a la meva xarxa wifi,després si faig ** iwlist scan** no funciona,només surt la xarxa a la que estic connectat.
En canvi si estic des-connectat si que em busca les xarxes wifi que hi ha al voltant.
¿?..

1. Sí, se'n va.
2. Sí, aquest model ho fa així.

:-D

---

### Post by climent on 2007-12-09
Sembla que finalment he aconseguit fer funcionar la wifi!!!! A veure, fent les prevencions que no domino ni de bon tros el tema linux, m'he arriscat i he fet un "mix" entre l'adreça que en un post anterior comentava en Papapep i l'adreça "znote4200.linux.dk". Vaig començar fent una nova instal·lació de Gutsy (i en porto ja quatre), i anant a descarregar les acerkeys (de Sourceforge.net, les que en CarlesOriol diu que només serveixen per les tecles especials). Doncs bé, pel que he pogut saber, el botó que apaga i engega la wifi actua per software. Un cop instal·lades les acerkeys, és quan he anat a l'adreça que comento, la znote, i he anat seguint a partir del quart punt (m'ha semblat que els anteriors no serveixen) i, he de dir que porto ja quatre dies a ple rendiment. De fet, aquest post l'escric a 10 metres del router i amb bateria, i que apago i engego quan vull.
Potser fora bo que algú més coneixedor que no pas jo, també ho provi i pugui fer un howto més acurat que el meu.
Gràcies a tots.

---

### Post by climent on 2007-12-13
.

---

