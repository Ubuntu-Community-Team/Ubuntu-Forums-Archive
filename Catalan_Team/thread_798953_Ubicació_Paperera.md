---
title: "Ubicació Paperera"
date: 2008-05-18
forum: Catalan Team
---

### Post by Rubunter on 2008-05-18
Avui anant a borrar el contingut de la paperera m'he trobat que la carpeta .Trash que solia tenir dins el home amb el Gutsy ja no hi es. Ara la ubicació de la paperera és trash://. On para això dins de l arbre de directoris? I a què és degut aquest canvi?

En el remot cas  que volgues tornar a relacionar la paperera amb la carpeta .Trash de dins el meu directori personal...com ho podria fer?

---

### Post by papapep on 2008-05-18
A Hardy la paperera s'ha mogut a ~/.local/share/Trash.

---

### Post by LitusMayol on 2008-05-18
> **papapep said:**
> A Hardy la paperera s'ha mogut a ~/.local/share/Trash.

Escuet i eficient! 
Merci, és un dubte que jo també tenia... Però simplement pensava que era un empanat i que sempre havia anat així i no me'n deuria haver adonat.

---

### Post by Rubunter on 2008-05-18
> **LitusMayol said:**
> Escuet i eficient! 
Merci, és un dubte que jo també tenia... Però simplement pensava que era un empanat i que sempre havia anat així i no me'n deuria haver adonat.

Jo he arribat a pensar que tot havia estat un somni...que la carpeta .Trash mai havia existit. Ja puc dormir tranquil

---

### Post by ilku on 2008-05-19
Doncs, a més de nosaltres, el sistema tampoc sap on esta :)

Si fiqueu la icona a l'escriptori

Aplicacions-->Eines de Sistema-->Editor de configuració

Apps-->nautilus-->desktop-->(activem casella)trash_icon_visible

Resulta que la paparera no canvia l'icona quan esta plena tot i que a dins si que hi ha brossa.

Suposo que ja ho arreglaran

---

### Post by RainCT on 2008-05-19
Gràcies, papapep! Jo també m'estava preguntant on s'havia ficat...

Sembla que tenen previst afegir una opció per restaurar els fitxers esborrats; anem progressant :).


> **ilku said:**
> Resulta que la paperera no canvia la icona quan esta plena tot i que a dins si que hi ha brossa.

Doncs a mi em funciona perfectament. Però sí que hi ha una errada que fa que en algunes circumstàncies (pel que jo sé, desconegudes) la paperera no sàpiga que no està buida, així que suposo que deu ser aquesta la que t'afecta (però no és pas nou aquest problema, ja fa temps que hi és).

En particular, és aquest: [LP #34247](https://bugs.launchpad.net/bugs/34247).

---

### Post by CarlesOriol on 2008-05-19
L'ubicació .local és sol dels discs locals la resta es pot accedir per

trash:///

---

### Post by ilku on 2008-05-20
Ja,Ja,Ja...

Voleu riure una estona. Resulta que després de reiniciar si ha canviat la icona a paperera plena. Faix boto dret i buido la paperera. La meva sorpresa quan ara la icona del quadre es la que diu que esta plena.....
Ja se que reiniciant segurament es solucionara, però això no era d'un altre sistema :)

Si es que soc gafe i les coses mes rares em passen a mi (encara recordo l'ordinador que per canviar-lo de lloc va deixar de funcionar la configuració del teclat, algú d'aquí ja sap de que parlo).

---

