---
title: "[SOLVED] Evince"
date: 2007-12-31
forum: Catalan Team
---

### Post by prostata on 2007-12-31
Un cop he pogut fer un arxiu PDF a partir d'una URL, voldria saber el següent:

¿Cóm puc fer per treure les pàgines que no vull? per exemple, la pàgina 12-13-15 d'un document determinat no tenen cap interès per a mi. He provat amb botó dret del mouse, però res de res,

Gràcies per la vostra ajuda...

---

### Post by CarlesOriol on 2007-12-31
pdfedit

---

### Post by prostata on 2007-12-31
> **CarlesOriol said:**
> pdfedit

Si, si...ja he fet l'intent, però em dona aquest error:

error carregant doc. /xx/xx/xxx.pdf
CPdf open failed.reason=f parsing problem error Code=

en tenc el que hi diu però no sé com erreglar-lo, segur que tú si ;-) gràcies

---

### Post by CarlesOriol on 2007-12-31
Uops...

Lleig això!

He passat abans l'arxiu pel ps2pdf (ps2pdf arxiu1.pdf arxiu1_copia.pdf ) i l'ha obert sense problemes.

Pot ser que l'arxiu generat sigui més ps que pdf?

---

### Post by sianeu on 2007-12-31
Segueixo aquest fil amb interès. He instal·lat el pdfedit i em va bé amb els pdf descarregats. Però amb els que he creat jo de pàgines web (imprimint amb la impressora de pdf del sistema) tinc el mateix error. 

Salut

---

### Post by prostata on 2007-12-31
> **CarlesOriol said:**
> Uops...

Lleig això!

He passat abans l'arxiu pel ps2pdf (ps2pdf arxiu1.pdf arxiu1_copia.pdf ) i l'ha obert sense problemes.

Pot ser que l'arxiu generat sigui més ps que pdf?

podria ser, efectivament, malgrat que les propietats de l'arxiu hi diu xxx.pdf però entenc per la resposta que hi dona PDF editor segur que hi ha més de ps que pdf. Però, però Evince l'obra sense cap mena de problema ¿?, ¿qué fem....? ;-)

---

### Post by prostata on 2007-12-31
Carles...definitivament es PS, he vist en tipus document: PS malgrat que apareix l'extensió.pdf, ara que podria fer??

---

### Post by sianeu on 2007-12-31
Es cert. Els creats per mi, a propietats, diu que son "PS document". Com es modifiquen aquests?, o cóm crear autèntics pdf?

---

### Post by CarlesOriol on 2007-12-31
Home crec que recordant de fer un ps2pdf abans d'editar-lo pot ser suficient.

No sé si ho tinc mal entes però el pdf bàsicament és un tipus d'encapsulament de postscript per tant la rel del ps i del pdf son la mateixa. (Corretgiu-me si m'equivoco)

---

### Post by CarlesOriol on 2007-12-31
Vinga ULL VIU que va la solució:

Quan fem un document amb la impresora CUPS/PDF si diem que l'escrigui en un arxiu ens genera un arxiu ps (compte els usuaris d'acrobat en windows no el podran llegir).

Per tal de fer un pdf cal dir-li que imprimeixi normalment i despres recollir l'arxiu a la carpeta /home/usuari/PDF

Au. Espero que us serveixi.

---

### Post by orestesmas on 2007-12-31
Fer això ho veig molt més senzill: Imprimeix a PDF només les pàgines que vols (potser hauràs de fer una previsualització per saber quines són).

---

### Post by CarlesOriol on 2007-12-31
No no Orestes. El cups/pdf generarà un ps en qualsevol cas si ho enregistres en un arxiu. (si, ja sé que en kde amb el konqueror això no passa!).

---

### Post by sianeu on 2008-01-01
Ara a mi ja em va bé. Moltes gracies.

Salut

---

### Post by prostata on 2008-01-01
Doncs a mi no em funciona encara. Tinc tres impressores ¿? encara que no més faig servir una.

Hi surten:
CUPS/Z600 es la lexmark físicament 
CUPS/ImpressoraPDF  que la vaig crear ahir
CUPS/PDF que no sé que hi pinta
PostScript/Default

Fent proves de la segona fins a la quarta imprimint a fitxer directament sempre em dona com a resultat un  .PS

si no ho faig així simplement no en fa res de res...
quines suggerències em podria-ho donar??

---

### Post by sianeu on 2008-01-02
Jo de CUPS/PDF només en tinc una. La PostScript /default també la tinc, però no l'he feta servir mai. 

Jo si li dic d'imprimir amb la cups/pdf i no marco la casella d'imprimir a fitxer, em crea un pdf. Si marco la casella em surt un ps.

Si no et va bé, jo eliminaria les dues cups/pdf i la tornaria a crear.

Salut

---

### Post by prostata on 2008-01-02
Mira sianeu, jo he tingut sempre el problema amb l'assistent de instal-lació de la impressora. Per possar-te un exemple si mires aquí [http://www.guia-ubuntu.org/index.php?title=Instalar_impresora#Instalar_una_impresora_PDF](http://www.guia-ubuntu.org/index.php?title=Instalar_impresora#Instalar_una_impresora_PDF)
sembla ben fàcil ¿oi?, bé doncs és aquest el meu problema. que quan he volgut instal-lar  la cups-pdf l'assistent que surt és el que et poso més abaix. 

De fet ja he solucionat el problema, el que passa és que hagués volgut fer-ho com tu dius, però si no és d'una forma, és d'altre...

---

### Post by sianeu on 2008-01-03
A mi em surt el mateix assistent que a tu. Aquí li clico a nova impressora i escolleixo la pdf (print into pdf file) seguint el assistent.

La guia que has enllaçat potser es de una versió anterior del Ubuntu amb un assistent diferent.

Però si ja ho tens tot solucionat dons res, a gaudir-ho,  :popcorn:

Salut

---

### Post by papapep on 2008-01-03
Per possibles interessats, he creat un mini-article al meu blog al respecte:

[http://extralinux.net/?q=node/32](http://extralinux.net/?q=node/32)

---

### Post by prostata on 2008-01-03
> **papapep said:**
> Per possibles interessats, he creat un mini-article al meu blog al respecte:

[http://extralinux.net/?q=node/32](http://extralinux.net/?q=node/32)

Molt oportú papapep, ja que en aquest blog hi surt clarament la mancança que jo tinc i que no he sabut expressar de cap manera. 

Quan faig Afegir Impressora>dispositius>***Print into PDF file***

Doncs bé a mi no m'apareix de cap manera el Dispositiui>Print into PDF File

Per això no puc configurar com Deu mana.....Gràcies per aquesta aportunitat...¿com podria fer-lo???

---

### Post by papapep on 2008-01-03
Doncs ara no ho puc mirar (teòricament estic treballant), però aquestes captures són de una Gutsy nova de trinca a una màquina virtual, o sigui que tot això ve "de fàbrica".

---

### Post by prostata on 2008-01-03
T'annexo una captura que et donarà una idea clara de la meva situació...i també el gibbon és nou de fàbrica ;-) i com pots apreciar no hi surt Dispositius>Print into PDf file

---

