---
title: "[SOLVED] El Calc funciona bé, però no se com es fa...."
date: 2008-01-17
forum: Catalan Team
---

### Post by sianeu on 2008-01-17
Tinc un llistat de películes en varis fulls, unes en català i altres en castellà. El llistat català el tinc amb lletres de color blau, i negre el castellà.

Però quan els ajunto en un altre full i vull ordenarlos alfabèticament, el color de les lletres romàn al mateix lloc (com si fos una qualitat de les cel·les i no de les paraules).

Com puc fer que al ordenar, les paraules mantinguin el seu color encara que canviin de lloc?

Potser aquestes preguntes de programari no son adequades per aquest foro. Si es aixì, perdoneu.

Salut

---

### Post by papapep on 2008-01-17
Si quan les juntes a un altre full, al moment d'enganxar li dius que et copii el format, a més de fer l'enllaç, crec que aleshores et conserva el format en cas de reordenació.
No sé segur si és això el que volies dir.

---

### Post by sianeu on 2008-01-17
Si, es això. El que passa es que en se molt poc. No se com copiar el format (ni tampoc el enllaç). Jo seleecciono les files del primer full arrosegant sobre els números de fila, i botò dret/copiar. Vaig al full on ho ajunto, clico sobre el número de fila de la primera fila buida, i botò dret/enganxa. Faig el mateix amb el segon full, el tercer, i els que hi hagi.....

Al full de destí si que queda cada fila amb el seu color de lletra (em sembla que això vol dir que es copia el format, no es així?). Però al clicar ordenar (de A a Z) el color de cada fila es inalterable: si abans d'ordenar alfabèticament les files de 37 a 63 eran blaves, segeixen sent-ho després d'ordenar encara que el contingut hagi cambiat de fila.

---

### Post by papapep on 2008-01-17
És molt fàcil (i no pateixis, ningú ha nascut ensenyat ni ho sap tot, o sigui que estem en igualtats de condicions...) però cal saber on trobar-ho:

Quan has copiat el que vols i ho vas a enganxar, en vers de fer Ctrl+V, fes servir la combinació Maj+Ctrl+V i t'apareixerà el diàleg de la imatge adjunta.

Allà verifica que tinguis marcat "Enganxa-ho tot" i "Enllaç" i aleshores, si no vaig errat, et respectarà el format de la cel·la d'orígen facis el que facis amb la cel·la destí.

---

### Post by sianeu on 2008-01-17
Ja ho havia provat això (botò dret/enganxament especial), i després de la teva primera resposta també ho havia provat amb la casella *enllaç* marcada. No funciona.

A veure si serà problema del arxiu (el vaig transformar ja fa molt de temps del excel). Seria una feinada de c****ns!!!. Potser hi hauria alguna manera de tornar a donar format a tot per no haver-ho de tornar a escriure......

---

### Post by sianeu on 2008-01-17
He fet una prova amb un nou arxiu. 5 files a cada un dels dos primers fulls, un en negre i l'altre en blau. Ho he enganxat al tercer full amb la casella *enllaç* marcada, ordeno, i segueix fent el mateix (les 5 primeres d'un color i les altres 5 de l'altre).

Potser es el meu OpenOffice que no va bé.....

---

### Post by jodufi on 2008-01-18
Acabo de provar-ho i a mi em funciona sense cap problema. Haig de dir que ho he fet amb el finestres 2000, a la feina hem canviat a OpenOffice.org, però encara no a Ubuntu :)
Ho he provat amb "Enagnxa-ho tot" activat i amb "Enllaç" activat i desactivat. En els dos casos cap problema, també mou els colors.
Adjunto el fitxer on he fet les proves.
Si tens més problemes, adjunta un fitxer.

---

### Post by sianeu on 2008-01-18
He agafat el teu fitxer i he reordenat el full 3 al revés. Com pots veure, no ha conservat el color dels números.

No se si es problema del meu programa o del Ubuntu. Ho provaré a altres màquines.

Gracies per l'ajut.

Salut

---

### Post by sianeu on 2008-01-18
A l'altre màquina que tinc amb Ubuntu tampoc funciona. Així que deu de ser un problema de l'OpenOffice amb el Gutsy.

Si algú que sàpiga anglès pot comprovar-ho i reportar el problema.....

Salut

---

### Post by sianeu on 2008-01-18
Acabo d'instalar la versió 2.2  per windows (softcatala) i tampoc em funciona. Ja no se que pensar....

Si algú més pot provar-ho seria definitiu.

---

### Post by papapep on 2008-01-18
Doncs a Windows XP amb la versió 2.2 també em funciona correctament.
Potser estem fent un "diàleg de besugs" i no ens acabem d'entendre...
El fitxer que ha passat en jodufi tampoc et funciona correctament? A mi si...

---

### Post by sianeu on 2008-01-18
A mi no. Descarrego el fitxer a l'escritori, s'obre al full 3, clico sobre la columna A i clico a ordenar Z->A, el resultat el tens al adjunt.

També es sobre win XP. Aquest missatge l'escric desde XP.

salut

---

### Post by papapep on 2008-01-18
Ho sento en l'ànima, però a mi em segueix funcionant. Insisteixo en que alguna cosa es perd entre el que fas tu i el que fem nosaltres. T'adjunto el fitxer que has enviat modificat i que també em funciona ordenant per diferents criteris les dues columnes, les de números i les de lletres.

---

### Post by cortsenc on 2008-01-20
Jo ja no se ni de que esteu parlant.
M'ho he mirat jo i em pensava que no funcionava, però després he vist que si que funcionava el que crec que busca en Sianeu. A veure:

**Prengunta:** L'objectiu es que al ordenar-ho, els que abans estàven en blau, segueixin estan en blau?
O sigui, que el color de la lletra s'apliqui a la paraula i no a la cel·la?

Si és així, a mi m'ha funcionat amb **Ubuntu 7.10** i **OpenOffice.org 2.3**

Per cert, alhora de ordenar, et proposo que vagis a **DADES>ORDENA** i a la pestanya **OPCIONS** tinguis marcada la opció de **INCLOU FORMATS**.

I per comprovar que estem entenent el mateix, adjuntu una captura de pantalla on a la primera columna hi ha els nombres ordenats de forma **descendent**, que han conservat el seu color original. A la segona columna, hi ha el color que hi havia quan estaven ordenats de forma **ascendent**. No se si m'he explicat be.

---

### Post by sianeu on 2008-01-20
Efectivament, cortsenc, per aquest camí si que em funciona. Moltes gracies!!!!.

Jo pensava que els botons de les barres d'eines eren enllaços directes a les ordres de la barra de menú.

De tota manera, podries mirar si a tu et funciona prement el botó A->Z o Z->A de la barra d'eines?. 

Salut

---

