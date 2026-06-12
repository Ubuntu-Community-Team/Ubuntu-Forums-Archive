---
title: "[SOLVED] Problemes d'Actualització"
date: 2008-10-17
forum: Catalan Team
---

### Post by LitusMayol on 2008-10-17
Ei familia!

Escolteu tinc problemes al actualitzar des de fa tres o quatre dies. No en vaig fer cas, perquè a vegades al cap d'un parell de dies ja actualitza correctament. Però això ja em comença a preocupar, hi ha paquets que no em deixa actualitzar que fan pinta d'importants (veure el 1r adjunt).

El tema és que cada dia m'apareix el *Gestor d'Actualitzacions* a la barra de l'Escriptori amb una desena d'actualitzacions (veure el 2n adjunt). Aleshores quan hi clicko el *Gestor d'Actualitzacions* ja em dóna un missatge, que no mola massa, dient que "*No s'ha pogut instal·lar totes les actualitzacions*". Aleshores em dóna la opció de *Tancar* o bé d'"*Actualització parcial*"(veure el 3r adjunt). Si tanco, tanca. Si actualitzo de forma parcial, fa com si actualitzés (4t adjunt), però al final no ho fa (últim adjunt).

No sé em té preocupat. Algú em pot ajudar?

Merci

---

### Post by tanreb20 on 2008-10-17
Hola LitusMayol!

A mi em passa sovint, no sé ben bé que faig, pero solc fer un

```
sudo dpkg --configure -a
```

Aixo en principi m'arregla les coses.

Sino desde synaptic, amb el **filtre trencats**, potser!

Sino l'altre que et puc dir es que inicis amb **mode recovery**, i intentis fer anar un **dpkg (una de les 4 opcions que et dona la consola)**, hauries de tenir conexio a internet per fer-ho segurament. Si ets wifi prova de conectar-lo a cable i en principi anira :S

---

### Post by LitusMayol on 2008-10-17
Ep!

El:
```
sudo dpkg --configure -a
```
no ha fet efecte... No sé simplement m'ha demanat la contrasenya i prou. No ha passat re més. Se'm manté la icona i la problemàtica.

Amb elk **Synaptic** el filtre trencats és buit! :S

Alguna idea?

(merci de totes maneres, **tanreb**)

---

### Post by PatrickVogeli on 2008-10-17
prova a fer un sudo apt-get update && sudo apt-get dist-upgrade

salut

---

### Post by tanreb20 on 2008-10-17
sudo aptitude update && sudo aptitude safe-upgrade && sudo aptitude dist-upgrade


per a millors resultats.

---

### Post by quitus on 2008-10-17
pots provar a canviar de servidor en les fonts de programari, a mi em va passar una cosa semblant i ho vaig arreglar així. posa el servidor principal i a veure que passa.

salut

---

### Post by LitusMayol on 2008-10-18
> **PatrickVogeli said:**
> prova a fer un sudo apt-get update && sudo apt-get dist-upgrade

salut

Simple i solvent.

Ha funcionat! Patrick, ets un crack!

Merci a tots!

---

