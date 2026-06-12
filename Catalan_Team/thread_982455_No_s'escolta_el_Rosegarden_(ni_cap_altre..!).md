---
title: "No s'escolta el Rosegarden (ni cap altre..!)"
date: 2008-11-14
forum: Catalan Team
---

### Post by blauigris on 2008-11-14
Hola nois i noies,

Tinc un petit problema. M'agradaria poder editar partitures i poder escoltar el que estic escrivint (no vaig passar de segon de solfeig...), i m'he instalat el Rosegarden (De fet me'ls he instalat tots, però aquest m'agrada bastant). El problema es que no txuta. 

Al principi em posava que era un error de que faltava el dimoni jack. Vaig instalar el Jack Control, o algo així, i ara ja no em dona aquest error, però segueix sense escoltar-se. He mirat aviam la configuració a settings, però segons ell està tot bé, de fet surt la barreta del volum movent-se i tot. 
Llavors he pensat que potser seria cosa de que tinc algun dispositiu del alsa en mute, i l'he obert amb l'alsamixer i els he posat tots al màxim, però ni així.
He pensat que potser era cosa del Rosegarden, però ni el Denemo ni el Musescore no van tampoc. Serà per que tinc el kernel genèric i no el low-latency? No ho crec.

Algú té alguna idea de que em pot estar passant o almenys per on podria començar a mirar. No em ve gens de gust tornar a composar amb Windows. :guitar:

Merci per tot.

Blauigris

---

### Post by papapep on 2008-11-14
Doncs podria ser per que Intrepid (i també Hardy abans) té el pulseadio com a servidor d'audio "preferit". A més crec haver llegit a algun lloc (potser la llista info?) que hi ha hagut un canvi important de llibreries referents a audio, i que els programes que no s'han posat les piles i han adoptat el canvi han fet salat i no poden funcionar com cal a la 8.10, o ho fan després de fer-te suar sang. 
Però recorda que parlo d'oïdes, que no ho és que ho sàpiga jo de primera mà. :-)

---

### Post by Pablitus on 2008-11-15
Hola Blauigris!

Pots mirar-te [això]("http://www.musix.org.ar/rosegarden-tutorial-es/chapter-1.html") i [això altre]("http://parumi.org/curso_produccion_musical_linux/capitulo4.html").

No crec que sigui necessari tenir el kernel-rt per a fer-ho funcionar.

Salut!

Pau

---

### Post by CarlesOriol on 2008-11-16
Per editar partitura et cal un sintetizador midi. Pots intra&#320;lar un per programari anomenat timidity.

Et caldrà dirigir la sortida del rosegarden als ports del timidity.

---

