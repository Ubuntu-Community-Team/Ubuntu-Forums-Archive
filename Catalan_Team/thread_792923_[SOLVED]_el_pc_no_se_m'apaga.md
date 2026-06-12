---
title: "[SOLVED] el pc no se m'apaga"
date: 2008-05-13
forum: Catalan Team
---

### Post by fonde on 2008-05-13
ei gent,

tinc el kubuntu hardy i cada cop que vull tencar el pc l'he d'acabar tancant pel botó del portatil perquè mai se m'atura si clico per tancar(apagar sistema).

a algu mes li passa això?sabeu què pot ser?

---

### Post by CarlesOriol on 2008-05-13
Això ho havia vist en versions anteriors d'ubuntu.

Digues quina versió del sistema tens i quin ordinador.

---

### Post by fonde on 2008-05-13
kubuntu 8.04
acer travelmate 5520

el kubuntu hi posa l'intenció, però es queda la pantalla en negre i el pc funcionant,

pot ser que sigui algun programa en execució que hauria de tancar?

gràcies ^^

---

### Post by papapep on 2008-05-13
I si vas a un terminal amb, per exemple, Ctrl+Alt+F1 i li fas un:

```
sudo halt
```

s'atura el sistema o no?

---

### Post by fonde on 2008-05-13
> **papapep said:**
> I si vas a un terminal amb, per exemple, Ctrl+Alt+F1 i li fas un:

```
sudo halt
```

s'atura el sistema o no?


si!!


no se si us servirà aquest detall:
fent servir la consola al apagar-se m'ha sortit l'emblema de kubuntu en comptes,intentan apagar-lo des de l'icona no em surt ni l'emblema

---

### Post by LitusMayol on 2008-05-14
> **fonde said:**
> si!!


no se si us servirà aquest detall:
fent servir la consola al apagar-se m'ha sortit l'emblema de kubuntu en comptes,intentan apagar-lo des de l'icona no em surt ni l'emblema


A mi això em va passar i durant mesos vaig fer servir "*sudo halt*"(apagar) i "*sudo reboot*"(reiniciar) perquè el botó hi era però no em feia cap cas. 

A mi se'm va solucionar amb les primeres actualitzacions de la Hardy. :S


(no és molt útil aquest post, oi?...)

---

### Post by fonde on 2008-05-14
xD

home almenys serveix per saber que no sóc l'únic que l'hi ha passat

gràcies man
de mentres aniré apagant i reiniciant pel terminal...si trobeu alguna cosa al respecte ja m'ho direu! :)

---

### Post by lluisanunez on 2008-05-15
Si és per culpa d'un programa o un servei que per alguna raó no es pot aturar, potser trobaràs informació als logs del sistema, al menú d'administració.

---

### Post by fonde on 2008-07-06
com va pronosticar en LitusMayol al actualitzar el nucli del kubuntu se'm va solucionar!

:S ja no pensava en què aquest fil havia quedat pengim-penjam

---

