---
title: "no puc veure videos amb avidemux"
date: 2008-04-20
forum: Catalan Team
---

### Post by niculau on 2008-04-20
Hola

si modifico algun vídeo amb avidemux, l'arxiu resultant no el puc reproduir amb el reproductor de sobretaula, de fet ni me'l detecta (no apareix l'arxiu)

el reproductor pot reproduir divx

potser el problema be del encapsulat avi?

---

### Post by CarlesOriol on 2008-04-20
No. L'encapsulat funciona bé. Digues quina configuració de codecs uses amb quins paràmetres.

---

### Post by niculau on 2008-04-20
La meva intenció era treure un dels 2 àudios disponibles en un vídeo .vob, (que puc reproduir en una ps3 però no puc canviar l'àudio) així doncs he deixat la opció "copy" en vídeo i àudio, desprès en seleccionar auto/dvd m'ha canviat el video a dvd(lavc) i el format de sortida a passat a ser "mpeg ps a+v" Selecciono l'àudio que m'interessa i deso l'arxiu.

fins aquí tot correcte, reprodueixo l'arxiu amb vlc sense problemes i amb els canvis que he fet, però en posar-ho a la ps3 no em reconeix l'arxiu, tot i que no observo diferencies entre l'arxiu original i el modificat.

fa temps vaig fer altres proves amb arxius divx amb el mateix resultat, per això pensava que era cosa del encapsulat o algun canvi no observable (a simple vista)

Ara recordo, vaig incrustar subtítols en un vídeo i desprès no vaig poder reproduir-lo amb el reproductor de sobretaula.


alguna manera d'analitzar amb més profunditat els arxius per veure quines diferencies hi ha?

---

### Post by quitus on 2008-05-07
Ja està solucionat.

Resulta que al anomenar els arxius de avidemux m'oblidaba posar la etiqueta .avi al final del nom amb la qual cosa el gamarús del reproductor no el reconeixia com a tal.
La descoberta de tot plegat ha sigut gracies a "themonospot" un programa d'anàlisi d'arxius avi que tampoc me'ls reconeixia.


Merda, ara no se com collons es posa [SOLVED] ho sento

---

