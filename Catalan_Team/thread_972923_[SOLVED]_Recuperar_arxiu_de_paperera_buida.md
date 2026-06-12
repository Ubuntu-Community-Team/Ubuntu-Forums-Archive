---
title: "[SOLVED] Recuperar arxiu de paperera buida"
date: 2008-11-06
forum: Catalan Team
---

### Post by prostata on 2008-11-06
Per error vaig enviar un arxiu a la paperera i a més la vaig buidar més tard.¿hi ha alguna forma/eina per poder recupera-lo? 

Gràcies

---

### Post by oriolsbd on 2008-11-06
Hola,

Prova el programa photorec de la suite testdisk. Jo no l'he utilitzat mai, però fa bona pinta:
[http://joinfreesoftware.blogspot.com/2008/10/recuperar-arxius-esborrats.html](http://joinfreesoftware.blogspot.com/2008/10/recuperar-arxius-esborrats.html)

El que sí està clar és que, quant més treballis amb l'ordinador, més probable serà que no el puguis recuperar.

Ja diràs què tal va el programa. :-)

---

### Post by prostata on 2008-11-07
Doncs el programa és una mica "complicat" no te cerca per extensió per exemple el meu arxiu era un .jpg i per trobar-lo  ha estat molt, molt de temps, però el pitjor no és pas això, es que quan he fet la cerca disponia de 56Gb a la partició i ara el nautilus em mostra només 15 Gb disponibles, ¿on son la resta fins als 56 si un cop recuperat l'arxiu tota la resta de la cerca l'esborrat?? i ara ¿com puc fer per recuperar tot aquest espai aparentment "perdut"??

Gràcies

---

### Post by oriolsbd on 2008-11-07
Hola, he provat jo també el programa, i realment et recupera TOTS els fitxers que troba "perduts" de la partició que li indiques (no he trobat la manera de filtrar els fitxers a recuperar). En un dels passos, li has indicat en quin directori t'ha de restaurar els fitxer. Allà hi tindràs un munt de fitxers, que són els que t'ocupen tot aquest espai.

---

### Post by prostata on 2008-11-07
> **oriolsbd said:**
> Hola, he provat jo també el programa, i realment et recupera TOTS els fitxers que troba "perduts" de la partició que li indiques (no he trobat la manera de filtrar els fitxers a recuperar). En un dels passos, li has indicat en quin directori t'ha de restaurar els fitxer. Allà hi tindràs un munt de fitxers, que són els que t'ocupen tot aquest espai.

Gràcies company...ja l'he solucionat. Tot el que hem dius ja ho he fet per recuperar les arxius, el problema com et dei, es que en esborrar tots aquets directoris que esmentas, ha sigut quan, i no se perquè, m'ha reduit de 55Gb a 15GB. el quehe fet ha estat el seguent:

sudo nautilus en un terminal,
Raiz /
root
.local
share
trash
files

Aquest és el camí i dins de /files hi eren tots els ariux repetits, per tant els hi esborrat del home, que és on es van colocar, però el que no sabìa és que a més es col-locaven també en la ruta que te esmento.
Gràcies per la teva col-laboració.
Aquí hi és tot.

/root/.local/share/Trash/files

---

