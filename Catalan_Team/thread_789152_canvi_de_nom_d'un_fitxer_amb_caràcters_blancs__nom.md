---
title: "canvi de nom d'un fitxer amb caràcters blancs / nom de fitxers des de f-spot"
date: 2008-05-10
forum: Catalan Team
---

### Post by lpargemi on 2008-05-10
Hola

Estic organitzant des de f-spot les meves fotografies, i gestionant les que descarrego des de la càmera.

A vegades em cal modificar una foto -correcció de colors, enquadrament, etc- normalment perquè la foto original està malament. Un cop assumit el canvi f-prot conserva dues fotos: l'original que es diu -per exemple- DSNC0767.JPG i   el modificat que es diu DSNC0767 (Modificat).JPG

Quan l'original no té més valor que la modificada n'hi ha prou amb guardar la modificada. Per aquests casos volia fer-me una mena de procés automàtic. Des del programa sqlite3 puc aconseguir la llista de noms a fitxers per esborrar i per canviar el nom. El problema és que no hi ha manera de canviar (amb mv) el fitxer que té un espai en blanc pel mig, perquè es pensa que son dos fitxers diferents.

Hi veig dues solucioons, però no sé com fer-ne cap de les dues:

1. Com es pot fer perquè f-spot no posi l'espai en blanc al nom (i de forma opcional sense els parèntesi)?

2. tinc -després de passar sqlite3 i fer un paste-, un fitxer (dit NomsPerCanviar.txt) amb els parells de noms de noms a convertir: p.ex "DSNC0767 (Modificat).JPG" "DSNC0767.JPG". No aconsegueixo que em funcioni l'ordre següent:

*grep -v zz NomsPerCanviar.txt | xargs mv*

Em diu que no existeix el directori DSNC0767.JPG. En canvi entrat-ho a mà línia a l&#324;ia si que funciona, però és un conyàs!

També ho he provat sense cometes, i em passa el mateix. (Entrant-ho a mà sense cometes es pensa que vull moure dos fitxers a un directori que tampoc existeix)

Alguna idea?

Agraït -i disculpeu pel rotllo-. 

Lluís

---

### Post by aswinms on 2008-05-10
In English please? or can we have this translated by somebody?!

---

### Post by lpargemi on 2008-05-10
> In English please? or can we have this translated by somebody?!

Sorry, aswinms, but this forum is in catalan (I guess)

Unfortunatelly I'm not capable to write this in english

Lluís

---

### Post by orestesmas on 2008-05-10
Ai, lluís, has caigut al costat fosc...

Ja has donat una oportunitat al Digikam?

Respecte a l'ordre grep/xargs, jo no he usat mai xargs, però la pàgina del manual parla d'una opció "-0" que cal passar a xargs per tal que no consideri que els espais en blanc acaben una línia... (o quelcom així)

---

### Post by lpargemi on 2008-05-10
Això de l' f-spot no era el que venia amb l'ubuntu?

Potser el vaig carregar fa tan temps que ni me'n recordo, però el cas és que ara ja mig sé com va...

Provaré, però, què sap fer el Digikam, perquè f-spot tampoc és que sigui la joia de la corona.

Lluís

Veig, després, que això és amb KDE, i que em demana el kdedesktop, que jo tinc, perquè ja em costa prou amb un sol escriptori... a veure què passarà.

---

### Post by RainCT on 2008-05-10
Si fas un mv normal, has de posar els noms de fitxer que continguin espai entre comentes (per exemple: mv "fitxer original.txt" "fitxer final.txt").

Si ho fas amb un xargs, has d'utilitzar la sintaxi «xargs -i <ordre> '{}'» (per exemple: grep -v zz NomsPerCanviar.txt | xargs -i mv '{}'). Alternativament, sembla que l'opció que comenta l'Orestes (grep -v zz NomsPerCanviar.txt | xargs -0 mv) també funciona.

---

### Post by lpargemi on 2008-05-11
Hola

He provat les dus coses, i no acaben d'anar

Us enganxo el què:

> 
grep -v zz CanviNom.txt | xargs -i  mv '{}'
mv: manca un operand fitxer destí després de «”DSCN5303 (Modificat).JPG” ”DSCN5303.JPG”»
Proveu «mv --help» per obtenir més informació.
mv: manca un operand fitxer destí després de «”DSCN5304 (Modificat).JPG” ”DSCN5304.JPG”»
Proveu «mv --help» per obtenir més informació.
mv: manca un operand fitxer destí després de «”DSCN5305 (Modificat).JPG” ”DSCN5305.JPG”»
Proveu «mv --help» per obtenir més informació.
(...)
etc


Amb -0 passa una cosa similar: s'embolica amb els canvis de línia \n:

> 
grep -v zz CanviNom.txt | xargs -0 mv
mv: manca un operand fitxer destí després de «”DSCN5303 (Modificat).JPG” ”DSCN5303.JPG”\n”DSCN5304 (Modificat).JPG” ”DSCN5304.JPG”\n”DSCN5305 (Modificat).JPG” ”DSCN5305.JPG”\n”DSCN5306 (Modificat).JPG” 
(...)
 ”DSCN5354.JPG”\n\n»
Proveu «mv --help» per obtenir més informació.



En fi, gràcies per l'interès i seguiré provant. I si m'en surto us ho explico.

Lluís

---

### Post by RainCT on 2008-05-12
Sembla que amb el -0 no et funcionarà, perquè passa tots els noms a una sola instància de mv, de manera que has de fer servir la forma «xargs -i <ordre> '{}'».

En quant a perquè no funciona aquesta, sembla que està considerant els dos noms com un de sol. Provaré a veure si se m'acudeix alguna solució.

---

