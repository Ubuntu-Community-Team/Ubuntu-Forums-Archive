---
title: "Envy ng - problema als repositoris"
date: 2008-04-06
forum: Catalan Team
---

### Post by CarlesOriol on 2008-04-06
Hola colla.

Com a fidel seguidor de l'envy de l'Alberto Milone per a la meva pobra màquina amb ati us comunico un bug a la versió actual: envyng  (la que 
 va partida en 3 paquets core, gtk i qt)

Un cop insta&#320;lat l'envy (cosa que farà perfectamen) tindrem problemes al fer l'actualització de repositoris.

Mirant els nostres sources.list no veurem res d'extrany i podem pensar que es un problema a la molta activitat que hi ha en actualitzacions aquest dies... però no ho és.

L'envy afegeix un arxiu de configuració al sources.list a la carpeta /etc/apt/sources.list.d anomenat envyng.list

i en aquest arxiu hi ha una referència al deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe per forçar la inclusió dels paquets univers... però que passa si usem un servidor diferent com es.archive o (com tinc jo per correr més) [ftp://archive](ftp://archive)...

Al fer l'update el apt trobarà les fonts duplicades i finalitzarà mostrant un error.

Per solucionar-ho sols al eliminar la linia deb [http://archive](http://archive)... del envyng.list.

Au... espero que serveixi.

---

