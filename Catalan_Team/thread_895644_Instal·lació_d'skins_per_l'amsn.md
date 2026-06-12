---
title: "Instal·lació d'skins per l'amsn"
date: 2008-08-20
forum: Catalan Team
---

### Post by tumateix on 2008-08-20
Hola,

Tinc un problema instal·lant skins (i també plugins) per l'amsn. Tinc l'arxiu corresponent descarregat i descomprimit, però en intentar-lo copiar al directori següent, no em deixa:

**/usr/share/amsn/skins**

Clicant a la carpeta amb el *botó dret -> Propierties -> Permissions* he mirat de canviar els permisos per a poder editar arxius a aquesta carpeta, però em diu que *"You are not the owner, so you can't change this permissions"*. El cas és que sí que sóc el propietari. Apareix com a propietari l'usuari **"root"**, i no sé com canviar-ho.

Una captura de pantalla [aquí]("http://img175.imageshack.us/img175/7991/screenshottd0.png").

Sóc nou en això de l'ubuntu però intueixo que aquest problema se'm repetirà sempre que intenti modificar una carpeta al directori **/usr**, i m'agradaria saber com solucionar-ho.

EDITO: efectivament, tinc el mateix problema amb qualsevol edició a la carpeta** /usr**. :(

Moltes gràcies de bestreta.

---

### Post by patrickfromspain on 2008-08-20
Tal com et diu, tu no n'ets el propietari. El propietari es l'usuari root, i tu ets l'usuari pepito-de-los-palotes. Per poder escriure sota el directori /usr, ho hauras de fer com a root, o obrint una finestra de nautilus com a root: en un terminal, gksudo nautilus i poses la teva contrasenya d'usuari.

Es com a windows: si no entres com a administrador, no pots anar a panel de control i canviar res, o instal·lar segons quins programes. El problema de windows es que ningun respecta aixo i tothom entra i treballa amb drets d'administrador, sent molt facil petar el sistema. En linux aquesta jerarqui es respecta.

De totes formes, tot aixo no et fa falta, ja que pots instal·lar pells de l'amsn sota la carpeta /home/el-teu-usuari/.amsn/skins

---

### Post by tumateix on 2008-08-20
Moltes gràcies.

Finalment ho he fet a través del nautilus perquè per l'altre mètode veia l'skin al menú de selecció de l'aMSN però el seleccionava i no passava res.

---

