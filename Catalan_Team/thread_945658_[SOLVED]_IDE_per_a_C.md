---
title: "[SOLVED] IDE per a C"
date: 2008-10-12
forum: Catalan Team
---

### Post by Kette on 2008-10-12
Hola.
aquest missatge és per a demanar la vostre opinió sobre quin seria un bon entorn de programació per el llenguatge C a nivell molt bàsic. Tinc un petit problema de "consciència": estic cursant una assignatura de fonaments de programació a la UOC i m'he trobat amb que, tot i defensar el programari de codi obert, el programari que donen per a determinades assignatures corre sobre windows, (per aquesta assignatura ens donen el DevC++). He cercat sobre el tema a Sant Google i l'únic que he aconseguit es embolicar més la troca: he trobat dues opcions que el personal aconsella, l'Anjuta i l'Eclipse. He instal·lat l'Anjuta des de'l Synaptic i no el puc fer anar, em manca el paquet "autogen" que he trobat en format src.rpm i no sé com instal·lar-lo.
Per concretar, aconselleu-me per trobar una alternativa, de moment faig córrer el programet amb el Virtualbox.
Salut
Eugeni

---

### Post by CarlesOriol on 2008-10-12
El kdevelop pot ser una bona eina pel que cerques.

Però pensa el que vols dir exactament en un "nivell molt basic". Si el que vols fer es aprendre C (o c++) com indiques, amb el gedit en tens de sobres. A més et permetrà de comprendre tot el procés que envolta aquestes "IDEs". Mentre que si sols t'inicies a desenvolupar en entorns assistits per tu sempre serà un misteri el que fan paquets com l'autogen.

Karles

---

### Post by oriolsbd on 2008-10-12
Has provat l'altre programa que comentes? L'Eclipse. No sé què tal va, però l'he sentit anomenar bastant. En el CD que donaven a la UOC fa 2 semestres amb una distribució Ubuntu, em sona que hi venia aquest instal·lat, de manera que suposo que funcionarà directament si l'instal·les.

Salut!

---

### Post by orestesmas on 2008-10-12
Com t'aconsella el Carles, jo provaria amb el KDevelop. Certament t'amagarà tots els detalls de les autotools, però si t'estàs iniciant en això, més val que te les amagui perquè fins i tot gent amb experiència en programació no les acaba de conèixer a fons.

Precisament la gent del KDE, amb la versió 4 han abandonat les autotools per passar-se al "Cmake" que, segons diuen, és un altre món.

Quant a l'eclipse, originàriament era un entorn molt potent de desenvolupament de Java, programat en Java, però com que té una arquitectura d'endollables (plugins) molt flexible, li han afegit el suport per altres llenguatges. Però en si és bastant pesant. No sé ara, fa temps que no el provo.

---

### Post by ggoscarl on 2008-10-14
El Netbeans també va força bé, originàriament també és per java però amb els plugins fa gairebé de tot.

---

### Post by Kette on 2008-10-14
Primer de tot agrair-vos els vostres consells. El C a nivell molt bàsic vol dir que només el fem servir per a codificar i així poder comprovar el resultat dels exercicis que fem en llenguatge algorísmic, de fet la programació la fem en aquest llenguatge. Amb això vull dir que no estudiem directament el C, ho fem com a fet col·lateral, en l'anomenat "taller de C" explicant-nos els principals trets diferencials entre tots dos llenguatges.
Com a resultat del vostres consells m'he baixat tots el programes que m'heu recomanat i estic en fase de proves. De moment faré servir l'Anjuta, és el que m'agrada més.
L'Eclipse te un "plugin" per a programar en C i C++ però bàsicament és per a Java (JDK) i l'entreguen en el CD però nomès per a les pràctiques de Java i aixó toca, amb una mica de sort, el proper semestre.
Per a instal·lar l'autogen si de cas obriré un altre fil.
Mercès
Eugeni

---

