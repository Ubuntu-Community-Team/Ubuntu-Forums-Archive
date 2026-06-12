---
title: "Top, htop i conky donen diferents resultats."
date: 2008-09-07
forum: Catalan Team
---

### Post by Quepotser on 2008-09-07
Aquests últims dies he estat mesurant amb certa assiduitat algunes de les "contants vitals" del ordinador (memòria utilitzada, CPU emprada, nombre de tasques funcionant, etc.). Doncs bé, en cap dels tres programes que he fet servir, les dades que m'han proporcionat són les mateixes. En el cas de **htop** i de **Conky** tot i ser diferents, s'apropen bastant, però **Top** em dona uns resultats totalment fora de mida si els comparo amb els dels altres dos. Un exemple clar està en el que fa pel consum de memòria amb la mateixa quantitat de processos en marxa. El **Top** m'està donant 950 MB utilitzats en un moment donat i en aquest mateix moment el **Htop** i el **Conky** em diuen que tant sols se n'està fent us d'uns 250 MB.
Hi ha alguna explicació per això?

---

### Post by guillemsola on 2008-09-07
Hola, crec que per la manera com linux administra la memòria tendeix a fer servir tota la que hi al sistema abans de passar a fer ús de la swap.

Vull dir amb això que el que realment fa és anar agafant memòria nova cada vegada. No vol dir doncs que realment faci servir aquesta quantitat de memòria sinó que tot el que pot està "cachejat".

Htop si t'hi fixes dibuixa sovint quasi tota la memòria amb ratlletes però fa un distinció de colors entre la que realment està en ús i la cau. Top no fa aquesta distinció i per ell tota la memòria està en ús.

Això doncs que HTop dóna una informació extra més acurada. Si ho mires amb l'analitzador del sistema de GNome també fa aquesta distinció entre memòria en ús i memòria cau.

Espero haver-te ajudat.

Salut!

---

### Post by Quepotser on 2008-09-07
Doncs, sí. M'has ajudat. Moltes gràcies.

---

