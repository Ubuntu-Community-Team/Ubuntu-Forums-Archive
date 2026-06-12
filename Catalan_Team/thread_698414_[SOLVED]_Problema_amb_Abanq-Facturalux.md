---
title: "[SOLVED] Problema amb Abanq-Facturalux"
date: 2008-02-16
forum: Catalan Team
---

### Post by rajoar on 2008-02-16
Resulta que he volgut canviar els mòduls de facturació de l'Abanq (Farturalux-lite) per carregar-los en català i, no se ben bé com, m'he carregat el mòdul d'administració, que és l'únic que no s'ha d'eliminar. Ara em trobo que no se com arreglar-ho, ja que no hem deixa tornar a instalar el programa, ni se com desinstal·lar-lo per tornar-lo a instalar una altra vegada... A veure si en Carles em pot donar un cop de mà...
Si intento desinstal·lar-lo em dona aquest missartge:
ramon@ramon-desktop:~$ /usr/local/facturalux-lite/uninstall
Could not find a usable uninstall program. Aborting.
ramon@ramon-desktop:~$
Si el torno a instal·lar em diu que el programa base ja està instal·lat...

---

### Post by CarlesOriol on 2008-02-16
Que jo sapiga els mòduls insta&#320;lats es carreguen directament a la base de dades. Els arxius del disc son per la creació de noves bases.

Per tant creant una base de dades nova hauria de ser suficient. 

Per desinstalar en plan bèstia pots eliminar la carpeta que dius i tornar-ho a crear tot.

---

### Post by rajoar on 2008-02-16
Efectivament després de:
dropdb facturalux
i tornar-la a crear... tot solucionat...
Mil gràcies

---

