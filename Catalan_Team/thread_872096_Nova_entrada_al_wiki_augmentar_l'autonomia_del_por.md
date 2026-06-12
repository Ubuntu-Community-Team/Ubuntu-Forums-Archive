---
title: "Nova entrada al wiki: augmentar l'autonomia del portatil"
date: 2008-07-27
forum: Catalan Team
---

### Post by patrickfromspain on 2008-07-27
Hola gent.

Acabo de crear un nou article al wiki, de moment completament incomplet, on intentare donar alguns trucs per augmentar l'autonomia d'un portatil. En aquesta entrada tenia previst de donar alguns trucs comuns, analitzar el powertop i el lm-profiler, així com un tutorial per reduir el voltatge d'alimentació del processador en portatils.

Com sempre, obert a suggerencies, correccions, adicions i el que convingui.

salut!

[https://wiki.ubuntu.com/CatalanTeam/Recursos/IncrementarAutonomiaPortatil](https://wiki.ubuntu.com/CatalanTeam/Recursos/IncrementarAutonomiaPortatil)

---

### Post by LitusMayol on 2008-07-27
Renoi **Patrick**, *cullunut*!

---

### Post by Frealof on 2008-08-02
Ei! 

Molt bona idea Patrick! Hi faré un cop d'ull i si no entenc alguna cosa (molt probablement) ja ho faria saber.

Salut!

---

### Post by patrickfromspain on 2008-09-02
Bé, en principi per part meva dono per conclosa la feina. Ha quedat una entrada bastant extensa i amb bastanta informació.

El problema que li veig es que provablement ha quedat tot bastant espes, si algu hi donés un cop d'ull... merci

salut

[https://wiki.ubuntu.com/CatalanTeam/Recursos/IncrementarAutonomiaPortatil](https://wiki.ubuntu.com/CatalanTeam/Recursos/IncrementarAutonomiaPortatil)

---

### Post by papapep on 2008-09-02
Abans que res he canviat el nom a la pàgina, que portava molts problemes amb espais i apòstrofs. Ha quedat així: CatalanTeam/Recursos/IncrementarAutonomiaPortatil

Quan creeu pàgines recordeu no deixar espai entre paraules i posar en majúscules les inicials (gairebé Java style :-)).

Quan pugui em miro la resta.

---

### Post by papapep on 2008-09-02
Ja m'ho he mirat. Molt bé Patrick, estàs d'un productiu que tombes...;-)

---

### Post by SiscoGarcia on 2008-09-02
Chapeau, Patrick.

Només dues coses:

He modificat el que deies als [requisits]("https://wiki.ubuntu.com/CatalanTeam/Recursos/IncrementarAutonomiaPortatil#Requisits") sobre el **mòdul acpi-cpufreq** quan al final deies que "si no és el vostre cas, ho sento, aquest tutorial [COLOR="Red"]no[/COLOR] us farà servei", hi he afegit el NO, si m'he colat digues-ho i ho canvio ràpid.

Un detall que he observat i no he gosat modificar perquè no tinc clar si fer-ho o no és que a l'apartat d'Altres [eines]("https://wiki.ubuntu.com/CatalanTeam/Recursos/IncrementarAutonomiaPortatil#Eines") i consells parles de l'eina **lm-profiler**, i dius que s'executa des d'un terminal amb l'ordre lm-profiler, però no hi dius que s'ha de fer com a root. Creieu convenient que hi digui o potser no cal i ja ho veurà l'usuari?

En fi, una gran tasca i una gran "currada".

Gràcies ;)

---

### Post by lo gambusí on 2008-09-02
Hola, Patrick, molt interessant això que has penjat.

He estat fent-ho seguint los teus passos, però m'he quedat aturat en una part, més per temor a fer alguna que no toque que no per no saber com continuar.

Concretament, un cop fet el > sudo ./linux-phc-optimize.bashi el > burnMMX, moment en el qual se m'hauria de penjar l'ordinador (cosa que no fa).

Llavors he pensat de continuar igualment, com dius, copiant els resultats del fitxer de text que s'hauria d'haver creat a l'escriptori (perquè és on he descomprimit els arxius descarregats), però no trobo este fitxer. 

A l'escriptori tinc los següents arxius: *phc_tweaked_vids* -arxiu de text en blanc-, *phc_cur_pos* -arxiu de text on només hi apareix un zero(?)- els executables *linux-phc-optimize.bash* i *functions.bash* i les carpetes *acpi-cpufreq* i *linux-source-2.6.24*.

Espero haver-me explicat bé...

---

### Post by patrickfromspain on 2008-09-03
lm-profiler, va com a root? no m'en recordo. Si es aixi, a canviar-ho :)

respecte a fer sudo ./linux-phc-optimize.bash i burnMMX: hauries de veure, en el terminal del optimize, que va fent coses, baixan numeros, en plan 40 39 37 si arriba a 0 o -1 i el pc no s'ha penjat, no passa res, significa que per aquella freqüencia la cpu pot estar alimentada al minim, que es el 19.

Ara, si la freqüencia a la que et pasa es la mes alta (en el meu cas 1,67GHz), doncs totes les freqüencies mes baixes funcionaran be amb 19 tambe.

salut

---

