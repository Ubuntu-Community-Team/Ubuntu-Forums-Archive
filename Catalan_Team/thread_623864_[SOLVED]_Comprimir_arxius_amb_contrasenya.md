---
title: "[SOLVED] Comprimir arxius amb contrasenya"
date: 2007-11-26
forum: Catalan Team
---

### Post by Curial on 2007-11-26
Déu vos guard,

Normalment comprimeixo arxius al format .rar

Tot i que no he tingut cap tipus de problema a la hora d'obrir-los (tant amb contrasenya com sense), sí que m'he trobat però, que al comprimir un arxiu qualsevol no he trobat la manera de protegir-lo amb contrasenya.


L'aliplicacions que faig servir és la File Roller 2.20.1.

Gràcies.
:)

---

### Post by jerec on 2007-11-26
File roller es un "Archive Manager" per l'entorn Gnome.  El que vol dir que ell tot sol no comprimeix ni descomprimeix res, necessita del programa adecuat per fer-ho (ex: unrar o rar per els fitxers rar)

-Necessites tenir instal.lat el programa "rar" (important!)
-A la interficie de File-roller, tria "Nou"
-Tipus arxiu "RAR" i li dones un nom "fitxer.rar"
- Al menu "Edita" selecciones "Contrasenya" i hi poses la paraula clau que et sembli
- Afegeixes els arxius que vols comprimir i tanques.

Ja tens el fitxer .rar amb contrasenya.

Desde la consola:
rar a -p fitxer.rar * (et demanara el password). 
Repassa "man rar"

---

### Post by Curial on 2007-11-27
Moltes gràcies jerec,

La veritat és que no m'ha funcionat tal com em deies però gràcies al que has comentat he trobat una altre camí:

He obert el gestor d'arxius File Roller 2.20.1 i he arrossegat el directori que m'interessava comprimir a dins de la finestra oberta d'aquesta aplicació. Un cop creat l'arxiu he anat a edita i he seleccionat la contrasenya. Un cop introduïda la contrasenya he fet un anomena i desa i he sobreescit l'arxiu.

El més curiós és que no m'ha funcionat fins que no he tret aquest directori de la partició NTFS, o potser a estat al desar-lo fora d'aquest partició, (no ho sé).

Ara només em resta blocar el contingut, és a dir, quan intetem obrir l'arxiu comprimit, que no s'hi vegi el contingut, però això ja són figues d'un altre paner.

Salut.

---

