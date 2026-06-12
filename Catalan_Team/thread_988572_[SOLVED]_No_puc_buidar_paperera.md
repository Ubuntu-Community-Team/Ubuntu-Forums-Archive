---
title: "[SOLVED] No puc buidar paperera"
date: 2008-11-20
forum: Catalan Team
---

### Post by sakuraya on 2008-11-20
Bona nit.

Ja fa un munt de dies que tinc la paperera plena d'arxius que he eliminat, però el problema és que no la puc buidar. He provat d'eliminar arxius individualment, per carpetes, canviant les propietats... sempre em surt el missatge: permission denied.

Algú sap com la puc buidar? Moltíssimes gràcies.

Salutacions a tothom.

---

### Post by torracastanyes on 2008-11-20
Si vas eliminar els arxius com a root, per llançar-los també has d'estar com a root. 
Pots obrir el terminal i escriure "sudo nautilus", i després buscar la paperera i buidar-la
En aquest fil trobaràs la ruta per arribar-hi:

[http://ubuntuforums.org/showthread.php?t=798953&highlight=paperera](http://ubuntuforums.org/showthread.php?t=798953&highlight=paperera)

---

### Post by sakuraya on 2008-12-03
He trigat una mica a poder solucionar-ho pero a la fi ho he aconseguit. Moltes gràcies torracastanyes, m'has donat la solució necessària. Com a detall diré que, potser és una tonteria, però un cop trobada la carpeta trash, no me la vinculava amb la icona perquè estava escrita en majúscula: Trash. Doncs he modificat i punt. Perfecte. Gràcies.

---

### Post by Druiling on 2009-01-04
Hola i perdó per reobrir un fil tancat però és que no m'ensurto.
Em passa el mateix. No puc esborrar alguns fitxers que tinc a la paperera.
He provat això del nautilus i si, em diu la ruta (trash:///), però no sé què mes fer des d'aquí.
Seríeu tan amables de guiar-me?
Gràcies per endavant.

---

### Post by papapep on 2009-01-04
Hauríem de buscar bé al fòrum abans de preguntar ;-) Posant un simple "trash" al buscador del fòrum, surten unes quantes ocurrències sobre el tema.

A **~/.local/share/Trash/files** haurien de ser els fitxers de la paperera del teu usuari.

---

### Post by Druiling on 2009-01-04
Gràcies-

---

### Post by papapep on 2009-01-04
Si et torna a passar, hauries de revisar els permisos d'aquest directori, ja que no és normal que no els puguis esborrar.

---

### Post by Druiling on 2009-01-04
Gràcies altre cop.

---

