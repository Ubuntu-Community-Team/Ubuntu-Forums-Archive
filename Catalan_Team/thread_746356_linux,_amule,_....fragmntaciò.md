---
title: "linux, amule, ....fragmntaciò"
date: 2008-04-05
forum: Catalan Team
---

### Post by sianeu on 2008-04-05
Conec la manera eficient en que linux organitza els fitxers. Però hi ha alguna cosa que no acabo de veure del tot clara. 

Tinc una màquina que fa us intensiu de amule, sobretot pelis. Com sempre en aquests casos el disc dur acaba omplint-se. Pero ja avans que això passi he estat descarregant per valor de 20Gb (en el moment que es completin totes les descarregues ocuparán 20 Gb) quan només me'n quedaven 15 de buides, i després només en queden 10, i després 5... I ja s'ha d'eliminar alguna cosa (el més antic, o el que té més fons, o el que menys m'agrada.....). I tornem-hi, un cop i un altre. Així, poc a poc, vaig substituint fitxers que linux havia conseguit mantenir sencers (els primers i fins arribar al voltant del 80% de la capacitat del disc dur) per altres de fragmentats (per falta d'espai lliure). Ara podria tenir el 50% del disc amb fitxers (videos) altament fragmentats.

Dues qüestions:
-algun programa que em digui el grau de fragmentació.
-es pot arreglar?

En aquest cas, al ser una partició de dades (/home), no afecta al sistema. Però si fos el mateix cas i no hi hagués partició de dades (amb la instal·lació i desinstal·lació  de programes pel mitg), no seria perjudicial per l'eficacia del sistema?

Perdó pel rotllo, però es una cosa que em pregunto de fa temps (concretament cada cop que he de "fer lloc" al disc dur :) )

Salut

---

### Post by elbuit on 2008-04-05
Anem a veure, segons comentes dius que coneixes la manera eficient en la que linux organitza els fitxers, així que no cal que et comente que ext3 (el que porta per defecte Ubuntu) no es propens a fragmentar-se, i dic que no es propens, no que no es puga arribar a un nivell de fragmentació no adequat.
Pots tindre un nivell de fragmentació del 10% i del ús quotidià al cap d'uns dies després baixar a un nivell de un 3%, ja que ext3 està dissenyat per a això.
Supose que vens del món de Windows, on la fragmentació era una cosa freqüent i per això disposa de gran quantitat d'eines per a defragmentar el sistema, també t'hauras adonat que en linux apenes existeixen, i el motiu és per que es poc habitual trobar un sistema fragmentat.

Una cosa que no li trobe massa sentit, es que afirmes que tens "un 50% del disc altament fragmentat" i no saps com veure el nivell de fragmentació.
Ho trobe incongruent, però de totes formes per a  respondre la teva pregunta quan es fa un fsck et mostra el grau de fragmentació (et diu un percentatge de fragmentació, ie: 3% non contiguous)

---

