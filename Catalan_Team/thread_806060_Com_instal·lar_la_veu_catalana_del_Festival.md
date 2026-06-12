---
title: "Com instal·lar la veu catalana del Festival"
date: 2008-05-24
forum: Catalan Team
---

### Post by friviere01 on 2008-05-24
Algú ha instal·lat la síntesi de veu en català?

Deixo els enllaços per si algú s'anima a escriure un ComEsFa detallat:

Presentació: [http://gps-tsc.upc.es/veu/festcat/](http://gps-tsc.upc.es/veu/festcat/)
Llegeix-me (Instal·lació): [http://www.talp.cat/festcat/download/LLEGEIX-ME](http://www.talp.cat/festcat/download/LLEGEIX-ME)
Documentació del Festival: [http://www.math.ias.edu/doc/festival-1.4.2/festival_toc.html](http://www.math.ias.edu/doc/festival-1.4.2/festival_toc.html)
Fil relacionat: [http://ubuntuforums.org/showthread.php?t=670457](http://ubuntuforums.org/showthread.php?t=670457)

---

### Post by CarlesOriol on 2008-05-25
Al mateix arxiu al punt 5. INSTA&#319;LACIÓ del LLEGEIX-ME diu on s'han de copiar els arxius per que funcioni.

---

### Post by friviere01 on 2008-05-25
**Solucionat!**

Doncs és que la instalació suggerida no em funcionava!

Si fem:
sudo apt-get install festival
i seguim les instruccions no em funciona (Ubuntu 8.04)

**En canvi si que em funciona fent:**

sudo apt-get install festival
sudo apt-get install festlex-cmu festlex-poslex festvox-kallpc16k libestools1.2

si ara seguim les instruccions per trobar la carpeta libdir:
~$ festival
Festival Speech Synthesis System 1.96:beta July 2004
Copyright (C) University of Edinburgh, 1996-2004. All rights reserved.
For details type `(festival_warranty)'
festival> libdir
"/usr/lib/festival"

i seguint les instruccions no funciona, per que les carpetes dicts i voices no es troben a /usr/lib/festival sinó a 

/usr/share/festival

que és on em sembla que cal instal·lar les veus catalanes. (es poden trobar aquí: [http://www.talp.cat/festcat/download.php](http://www.talp.cat/festcat/download.php))

Però tot i així donava aquest error:

~$ festival --language catalan
SIOD ERROR: unbound variable : voice_upc_ca_ona_hts
festival: fatal error exiting.

He instal·lat totes les veus, però em sembla que no és necessari (ja actualitzaré aquest punt)

**Corregint la ruta**
La documentació indica que la ruta de libdir és la font més comú de problemes, així, que seguint les instruccions arrenco festival indicant la ruta correcta:
~$ festival --libdir /usr/share/festival

I ara sí que em funciona!!!

Alternativa: per no haver d'indicar el libdir cada cop veieu això: [http://ubuntuforums.org/showpost.php?p=5039531&postcount=8](http://ubuntuforums.org/showpost.php?p=5039531&postcount=8)

**Exemples d'ús**
(Veieu també: [http://www.talp.cat/festcat/download/LLEGEIX-ME](http://www.talp.cat/festcat/download/LLEGEIX-ME))

festival --libdir /usr/share/festival --language catalan --tts arxiu.txt
echo hola mon | festival --libdir /usr/share/festival --language catalan --tts
cat arxiu.txt | festival --libdir /usr/share/festival --language catalan --tts

Cal que els arxius tinguin codificació latin-1

Les **instruccions originals** són aquí: [http://www.talp.cat/festcat/download/LLEGEIX-ME](http://www.talp.cat/festcat/download/LLEGEIX-ME)

**Nota: atenció amb les rutes al desempaquetar, un petit error em feia que no funcionés!**

**Millores:**
Si algú em pot indicar la forma d'indicar a festival la ruta carpeta libdir correcte sense haver-ho d'indicar cada cop que l'executem fent ~$ festival --libdir /usr/share/festival agrairé que ho indiqui per tal de millorar aquestes instruccions ComEsFa.

Caldria pendre nota per preparar una instal·lació amb arxius .deb

---

### Post by CarlesOriol on 2008-05-25
Collonut Paco.

Gràcies per la informació!

El fet que existeix aquest programa és un gran avanç i es podran fer grans coses.

(per exemple un freevial xerrat ... ;) )

---

### Post by friviere01 on 2008-05-25
**Integració amb kttsmgr (en preparació):**

Per poder fer servir les veus de forma interactiva amb kttsmgr cal fer:

~$ sudo gedit /usr/share/apps/kttsd/festivalint/voices

i afegir el següent després de l'etiqueta <voices> (i abans de l'etiqueta </voices>)

<voice>
  <code>upc_ca_ona_hts</code>
  <language>es_CA</language>
  <codec>ISO 8859-1</codec>
  <gender>female</gender>
  <preload>false</preload>
  <volume-adjustable>true</volume-adjustable>
  <rate-adjustable>true</rate-adjustable>
  <pitch-adjustable>true</pitch-adjustable>
  <name>Veu catalana - Ona</name>
</voice>

<voice>
  <code>upc_ca_pau_hts</code>
  <language>es_CA</language>
  <codec>ISO 8859-1</codec>
  <gender>female</gender>
  <preload>false</preload>
  <volume-adjustable>true</volume-adjustable>
  <rate-adjustable>true</rate-adjustable>
  <pitch-adjustable>true</pitch-adjustable>
  <name>Veu catalana - Pau</name>
</voice>

Tot i així, potser falta alguna cosa, ja que no em funciona. A veure si entre tots ho aconseguim!

Referències: [http://docs.kde.org/kde3/ca/kdeaccessibility/kttsd/using-kapp.html](http://docs.kde.org/kde3/ca/kdeaccessibility/kttsd/using-kapp.html)
Síntesis de voz en Gnome: [http://people.ofset.org/jrfernandez/edu/n-c/orca_3/index.html](http://people.ofset.org/jrfernandez/edu/n-c/orca_3/index.html) (¿Hay algún modo de acceder a gnome-speech directamente, para comprobar si está correctamente instalado y configurado?)

---

### Post by papapep on 2008-05-25
No hi ha cap fitxer de configuració del Festival on li puguis posar la variable aquesta d'entorn? Una altra manera, cutrilla, és fer un petit script en bash que l'invoqui amb l'afegit de la variable.

EDITO: He estat fent un cop d'ull a tot plegat.
Mirant la llista de fitxers que instal·la el Festival: [http://packages.ubuntu.com/hardy/i386/festival/filelist](http://packages.ubuntu.com/hardy/i386/festival/filelist)

n'hi ha un que m'ha cridat l'atenció de nom **init.scm** a **/usr/share/festival**, el qual diu al seu contingut:

```
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
;;;
;;;  Initialisation file -- loaded before anything else
;;;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

;;;  Basic siod library (need this before load_library or require works)
(load (path-append datadir "siod.scm"))

(defvar home-directory (or (getenv "HOME") "/")
  "home-directory
   **Place looked at for .festivalrc etc.**")

```

el qual sembla indicar que si crees un fitxer de nom .festivalrc dins el teu directori personal i hi poses la variable aquesta de la llibreria, és possible que funcioni.

---

### Post by friviere01 on 2008-05-25
Josep: Ho he intentat  amb .festivalrc però no m'he n'he sortit.
Però ja he aconseguit fer arxius de so. Faig un altre post!

---

### Post by friviere01 on 2008-05-25
**Com fer arxius de so (wav)**

Es pot aconseguir fent uns enllaços simbòlics així:

~$ cd /usr/lib/festival/
~$ sudo ln -s /usr/share/festival/voices
~$ sudo ln -s /usr/share/festival/dicts
~$ sudo ln -s /usr/share/festival/upc_catalan

Això també permet arrencar festival sense el paràmetres.

**Exemple d'ús:**
(Cal que l'arxiu tingui codificació latin-1)

Convertir un arxiu txt a wav

~$ text2wave -o arxiu.wav   -eval '(language_catalan)' arxiu.txt

**Per convertir a mp3**
Podeu fer servir lame així:

~$ lame arxiu.wav arxiu.mp3

---

### Post by papapep on 2008-05-25
Què has ficat dins el .festivalrc?

---

### Post by friviere01 on 2008-05-25
> **papapep said:**
> Què has ficat dins el .festivalrc?

(set! voice_default 'upc_ca_ona_hts')

---

### Post by friviere01 on 2008-05-25
**Problemes coneguts**

Si el text és molt llarg, s'obté aquest error:

SIOD ERROR: the currently assigned stack limit has been exceded

La única solució que he trobat, és dividir el text en altres més curts.

Alguna altre idea?

Referències: [http://www.cs.indiana.edu/scheme-repository/imp/siod.html](http://www.cs.indiana.edu/scheme-repository/imp/siod.html)

---

### Post by papapep on 2008-05-25
> (set! voice_default 'upc_ca_ona_hts')

No, si jo t'he dit el tema del .festivalrc per posar-hi la variable **libdir**.

---

### Post by friviere01 on 2008-05-25
> **papapep said:**
> No, si jo t'he dit el tema del .festivalrc per posar-hi la variable **libdir**.

No sé pas com es fa.

---

### Post by papapep on 2008-05-25
Doncs posant la variable dins el fitxer:

```
export libdir=path_que_posaves_al_executar_de_les_llibreries
```

---

### Post by friviere01 on 2008-05-25
**He fet un tutorial al wiki**

[https://wiki.ubuntu.com/CatalanTeam/SíntesiDeVeu](https://wiki.ubuntu.com/CatalanTeam/SíntesiDeVeu)

Agrairia si poguéssiu comprovar si us funciona.

---

### Post by SiscoGarcia on 2008-05-25
> **friviere01 said:**
> **Per convertir a mp3**
Podeu fer servir lame així:

~$ lame arxiu.wav arxiu.mp3

No vull tocar allò que no sona, però... seria complicat fer la conversió al format lliure .ogg?

EDITO: No serà tan senzill com "~$ lame arxiu.wav arxiu.ogg"?

---

### Post by friviere01 on 2008-05-25
> **papapep said:**
> Doncs posant la variable dins el fitxer:

```
export libdir=path_que_posaves_al_executar_de_les_llibreries
```

Doncs si ho vols provar fantàstic, jo ja tinc la meva instal·lació tan remenada...

EDITO: No em funciona. Mireu aquests exemples:
[http://gentoo-wiki.com/HOWTO_speechd](http://gentoo-wiki.com/HOWTO_speechd)

---

### Post by friviere01 on 2008-05-25
> **SiscoGarcia said:**
> No vull tocar allò que no sona, però... seria complicat fer la conversió al format lliure .ogg?

EDITO: No serà tan senzill com "~$ lame arxiu.wav arxiu.ogg"?

No crec que aquesta darrera solució serveixi (crec qeu lame és pel mp3)

La teva aportació em sembla molt important:
Està explicat aquí:
[http://ubuntuforums.org/showthread.php?t=175090](http://ubuntuforums.org/showthread.php?t=175090)
i aquí:
[http://dudas.wordpress.com/2006/12/13/ubuntu-facil-conversion-de-formatos-de-musica-mp3oggflacwav/](http://dudas.wordpress.com/2006/12/13/ubuntu-facil-conversion-de-formatos-de-musica-mp3oggflacwav/)

Si ho aconsegueixes es podria afegir al wiki: [https://wiki.ubuntu.com/CatalanTeam/SíntesiDeVeu](https://wiki.ubuntu.com/CatalanTeam/SíntesiDeVeu)

EDITO:
sudo apt-get install vorbis-tools
~$ oggenc arxiu.wav

---

### Post by Xispa on 2009-11-05
Hola,

torno a enfilar aquest fil de conversa perquè no aconsegueixo instal·lar les veus catalanes del festival. 

He seguit tant les instruccions facilitades pel Paco en aquest fil, les de [https://wiki.ubuntu.com/CatalanTeam/Tutorials/S%C3%ADntesiDeVeu](https://wiki.ubuntu.com/CatalanTeam/Tutorials/S%C3%ADntesiDeVeu) i també les de l'arxiu LLEGEIX-ME.txt que vénen dins de upc_ca_base.tgz

Pel que sembla ho tinc tot ben instal·lat (en referència a rutes on han de copiar-se els arxius i del tema del libdir). Ara bé, això és el que m'escup el terminal quan faig la primera prova:
```
jordi@iris:~$ echo hola mon | festival --language catalan --tts
param -l not of type float
SIOD ERROR:  
jordi@iris:~$
```
què vol dir això del param -l?
He fet un man de festival i no admet cap paràmetre -l. És a dir, entenc que no interpreta bé el paràmetre --language (si no l'hi poso, doncs va bé, però amb anglès).

Algú s'ha trobat amb la mateixa situació o té alguna idea respecte a què pot ser degut?

Per cert, tinc Hardy (estic esperant a la Lucid Lynx...)

Àpali,
Jordi

---

### Post by Xispa on 2009-11-23
Bé... doncs sembla que això del "param -l" no té res a veure amb l'execució directa de festival desde terminal. He iniciat el festival directament (sense paràmetres) i quan intento fer-li llegir un text en català, salta el mateix error:

```

jordi@iris:~$ festival
Festival Speech Synthesis System 1.96:beta July 2004
Copyright (C) University of Edinburgh, 1996-2004. All rights reserved.
For details type `(festival_warranty)'
festival> (language_catalan) 
catalan
festival> (SayText "Bon dia")
param -l not of type float
SIOD ERROR:  
festival> 

```

He buscat per St.google i em sembla que sóc l'únic de la Terra a qui li surt aquest error. 

Algú té alguna idea de què pot ser?

---

### Post by zeehio on 2009-12-29
> **Xispa said:**
> Bé... doncs sembla que això del "param -l" no té res a veure amb l'execució directa de festival desde terminal. He iniciat el festival directament (sense paràmetres) i quan intento fer-li llegir un text en català, salta el mateix error:

```

jordi@iris:~$ festival
Festival Speech Synthesis System 1.96:beta July 2004
Copyright (C) University of Edinburgh, 1996-2004. All rights reserved.
For details type `(festival_warranty)'
festival> (language_catalan) 
catalan
festival> (SayText "Bon dia")
param -l not of type float
SIOD ERROR:  
festival> 

```

He buscat per St.google i em sembla que sóc l'únic de la Terra a qui li surt aquest error. 

Algú té alguna idea de què pot ser?

Sí, t'explico:

Resulta que la darrera versió de les veus hts en català fa servir una versió més recent del Festival que la disponible a Hardy.

El paràmetre -l del que es queixa és un paràmetre intern d'un fitxer de configuració de la veu i que ha canviat al canviar la versió de festival. No té res a veure amb el "--language" com sembla que has vist.

Estic preparant-te un repositori de software per Hardy que t'hauria de permetre actualitzar el festival a la darrera versió i instal·lar-te les veus seguint el [tutorial](https://wiki.ubuntu.com/CatalanTeam/Tutorials/S%C3%ADntesiDeVeu#Instal%C2%B7lem%20les%20veus) (amb repositori i canviant jaunty per hardy on toqui).

Si encara llegeixes aquest fòrum, si us plau prova-ho. Si et sorgeix cap dubte, pregunta.

Disculpa les molèsties


=================

Aprofito per dir que corregit (tant al repositori com a la web de Festcat) el problema "Al pronunciar la lletra 'ñ' en algun nom propi forani, dóna aquest error" del wiki, de manera que probablement ja no és necessari tenir aquesta secció a "problemes coneguts".

---

### Post by Xispa on 2010-01-02
Merci zeehio. Ara funciona perfectament.
Després de fer una desinstal·lació manual seguint les instruccions de Desinstal·lació manual de [https://wiki.ubuntu.com/CatalanTeam/...3%ADntesiDeVeu](https://wiki.ubuntu.com/CatalanTeam/...3%ADntesiDeVeu), he afegit el repositori corresponent per a hardy, he fet
```

sudo aptitude install festvox-ca-upc-hts-ona

```
i oli en un llum.

---

### Post by friviere01 on 2010-01-02
Xispa: M'en alegro que les instruccions hagin estat útils.

M'agradaria documentar l'error de 'param -l not of type float', però no ho he entès. Podries explicar què és el que passava?

---

### Post by epileg on 2010-01-03
Bones,

Recentment he descobert aquesta fantàstica eina!

Ho tinc insta&#320;lat a ubuntu karmic amb els dipòsits del launchpad. Tot funciona correctament excepte les veus en format «clunits».

Quan provo de fer-ro servir em torna aquest error.

$ echo "Bon dia" | festival --tts --language catalan
Cannot open file /usr/share/festival/voices/catalan/upc_ca_mar_clunitsfestival/clunits/upc_ca_mar.catalogue as tokenstream
CLUNITS: Can't open catalogue file /usr/share/festival/voices/catalan/upc_ca_mar_clunitsfestival/clunits/upc_ca_mar.catalogue

com es pot veure, la ruta està mal definida a .../upc_ca_mar_clunitsfestival/... ja que la correcta seria .../upc_ca_mar_clunits/festival/... però no sé com corregir aquest error.

Gràcies.

---

### Post by zeehio on 2010-01-04
> **epileg said:**
> Bones,

Recentment he descobert aquesta fantàstica eina!

Ho tinc insta&#320;lat a ubuntu karmic amb els dipòsits del launchpad. Tot funciona correctament excepte les veus en format «clunits».

Quan provo de fer-ro servir em torna aquest error.

$ echo "Bon dia" | festival --tts --language catalan
Cannot open file /usr/share/festival/voices/catalan/upc_ca_mar_clunitsfestival/clunits/upc_ca_mar.catalogue as tokenstream
CLUNITS: Can't open catalogue file /usr/share/festival/voices/catalan/upc_ca_mar_clunitsfestival/clunits/upc_ca_mar.catalogue

com es pot veure, la ruta està mal definida a .../upc_ca_mar_clunitsfestival/... ja que la correcta seria .../upc_ca_mar_clunits/festival/... però no sé com corregir aquest error.

Gràcies.

Ara em poso a arreglar-ho. Miraré de pujar una actualització com abans millor.

Moltes gràcies per avisar.

Arreglat a festival-1.96~beta-11ubuntu0~ppa9

---

### Post by zeehio on 2010-01-04
> **friviere01 said:**
> Xispa: M'en alegro que les instruccions hagin estat útils.

M'agradaria documentar l'error de 'param -l not of type float', però no ho he entès. Podries explicar què és el que passava?

Documentar això potser és complicat.

Ho explico de diferents maneres, espero que alguna sigui entenedora. Cada explicació dóna més detall, però la primera hauria de ser suficient a efectes pràctics.

Explicació 1:
Els paquets de les veus catalanes HTS de Festival haurien de dependre d'una versió més moderna de Festival. Ho arreglo en la propera versió.
També cal dir que sense el repositori Festcat les noves veus HTS no funcionaran amb la instal·lació manual.

Explicació 2:
Les veus hts _noves_ *de Festcat* fan servir una versió més recent de Festival. Esperem que aquesta versió de Festival es publiqui oficialment com abans millor però de mentres hem de proporcionar la nova versió a través del repositori Festcat. Si fas servir la versió que proporciona Ubuntu de sèrie les veus no funcionaran correctament.

Explicació 3:
Festival passa internament al mòdul de síntesi uns paràmetres de configuració de la veu. El modul "vell" espera un paràmetre "-l" de tipus "coma flotant" mentre que el modul nou espera un paràmetre "-l" que pot ser vertader o fals (si no recordo malament). Per això es queixa de que el paràmetre no és del tipus esperat.

---

### Post by epileg on 2010-01-05
> **zeehio said:**
> Ara em poso a arreglar-ho. Miraré de pujar una actualització com abans millor.

Moltes gràcies per avisar.

Arreglat a festival-1.96~beta-11ubuntu0~ppa9

Ara funciona correctament, gràcies!


Salut i força,

---

### Post by zeehio on 2010-01-07
Comento alguns apartats de la guia que es poden actualitzar:

**Instal·lació**
Amb repositoris: Ara funciona per totes les versions, des de Hardy fins a Lucid (cal comprovar-ho).

Manual:
Al repositori s'ofereixen una bona mostra de les veus disponibles. Si volem provar més veus que no estiguin al repositori ho podem fer instal·lant-les de forma manual. *En tot cas* és necessari utilitzar el repositori Festcat per instal·lar Festival. (quan això canviï ho avisaré, però no depèn de mi i no hi ha data prevista de moment)

**Veu per defecte al iniciar Festival:**
La millor manera de triar una veu per defecte a partir d'ara és posant a "~/.festivalrc":
```

(set! catalan-default-voices (list 'upc_ca_ona_hts))

```
El motiu per aquest canvi és que es pretén que per cada llengua hi hagi una veu preferida.

**Configuració del dispositiu de so**:
[LIST]
[*]Si ets un usuari nou i fas servir PulseAudio,** [SIZE="4"]no cal fer res[/SIZE]**.
[*] Si ets un usuari nou i **no** fas servir PulseAudio (o PulseAudio et falla o tens problemes d'àudio):
En un terminal escriu:
```
sudo apt-get install alsa-utils
sudo printf ";use ALSA\n(Parameter.set 'Audio_Method 'Audio_Command)\n(Parameter.set 'Audio_Command \"aplay -q -c 1 -t raw -f s16 -r \$SR \$FILE\")\n" > /etc/festival.scm

```

[*]Si portes temps fent servir Festival, pots provar el nou mòdul posant un "[SIZE="4"];[/SIZE]" davant les línies dels fitxers /etc/festival.scm i ~/.festivalrc semblants a:
```

(Parameter.set 'Audio_Method [COLOR="Blue"]*alguna_cosa*[/COLOR])
(Parameter.set 'Audio_Command [COLOR="Blue"]*alguna_cosa*[/COLOR])

```
de manera que quedin:
```

;(Parameter.set 'Audio_Method [COLOR="Blue"]*alguna_cosa*[/COLOR])
;(Parameter.set 'Audio_Command [COLOR="Blue"]*alguna_cosa*[/COLOR])

```
[/LIST]
Les altres configuracions d'àudio no estan recomanades (tot i que poden funcionar).

**Exemples d'ús**
Per tal de sintetitzar text cal que estigui en codificació latin-1. Estem treballant per donar suport a UTF-8 però encara està disponible.

Per llegir "hola mon" podem fer a la terminal:
```
echo 'hola mon' | festival --language catalan --tts
```
padsp ja no és necessari, perquè tenim el mòdul natiu de PulseAudio.

Igualment, per llegir un arxiu de text (arxiu.txt):
```
festival --language catalan --tts arxiu.txt
```
o bé:
```
cat arxiu.txt | festival --language catalan --tts
```

**Codi per copiar al terminal:**
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A3A48C4A
source /etc/lsb-release
sudo echo "deb http://ppa.launchpad.net/zeehio/festcat/ubuntu $DISTRIB_CODENAME main" >> /etc/apt/sources.list
sudo apt-get update
sudo apt-get install festival festival-ca festvox-ca-upc-hts-ona
printf ";Catala per defecte:\n(set! language_default 'catalan)\n" > ~/.festivalrc

```

Podem provar que funciona amb:
```

echo 'hola mon' | festival --tts

```

**Com fer que festival llegeixi en altres idiomes**
Això està tot correcte, només caldria treure els "padsp" que no són necessaris.Per exemple:
```
echo hola | festival --language spanish --tts
```

**Tinc Ubuntu Hardy 8.04 i Festival no em funciona**
Aquesta secció ja no cal.

**Al pronunciar la lletra 'ñ' en algun nom propi forani, dóna aquest error**
Aquesta secció ja no cal.

**Amb algunes paraules, s'obté aquest error**
```
SIOD ERROR: the currently assigned stack limit has been exceded
```
El problema de les paraules com TamTam està resolt.
Si trobeu alguna frase problemàtica, són benvingudes al fòrum.

**Problemes coneguts:/Coses a fer:**
[LIST]
[*]Falta suport a UTF8. (Hi estem treballant)
[*]Cal poder pronunciar paraules amb caràcters estrangers.
[*]Tinc intenció de crear un paquet debian amb els scripts que hi ha al fòrum per posar-lo al repositori, de manera que es puguin actualitzar amb facilitat.
[/LIST]
=========
Suggereixo esborrar les seccions que ja no calen de la guia al final de tot, com alternativa també es podrien deixar al final de tot en un apartat "Problemes resolts".

---

### Post by zeehio on 2010-01-17
En la darrera actualització de Festival i Speech-tools he corregit un problema que hi havia amb les veus hts que feia que al sintetitzar un fitxer de text llarg el programa fallés. Gràcies a Paco Rivière (per adonar-se d'això i per molt més!)

**Més problemes coneguts:**
[LIST]
[*]Cal millorar el tractament de signes de puntuació:
[*]Sintetitzar 2 admiracions seguides "!!" no funciona bé.
[*]Problema si la frase comença amb I majúscula: SIOD ERROR: comma-not-inside-backquote 

[*]Donada una llista numerada de l'estil: 
```
1. Pomes
2. Peres
3. Plàtans
```
Sona així:
```
1. (PAUSA)
Pomes 2. (PAUSA)
Peres 3. (PAUSA)
Plàtans
```

[/LIST]

Cap al febrer em posaré a solucionar-los.

---

### Post by zeehio on 2010-03-20
Ara les veus catalanes funcionen amb UTF-8 i latin-1. Ara tampoc es pengen si no saben dir una lletra, simplement la ometen.

Seguim millorant coses, tot i que encara queda molt per millorar.

Sergio

---

### Post by ppyo on 2010-08-03
Y cómo hacer para usar **espeak** con *Freevial*?
:)

---

### Post by zeehio on 2010-10-10
Entre demà i demà passat em posaré a treballar per treure els paquets per Maverick.

No he pogut fer-ho abans.

Si voleu actualitzar i seguir utilitzant les veus catalanes, podeu fer servir el repositori de Lucid probablement i forçar la versió a la del repositori de FestCat.

Disculpeu el retard.

---

### Post by Darent on 2010-10-11
Baixant els paquets manualment per a lucid i instal·lant-los a maverick no funciona (almenys per a mi). Així que quan estiga llest per al 10.10 avisa si us plau.

Si a algú li interessa vaig fer un xicotet script que llegeix el que s'escriu a la terminal, sense necessitat de fer prèviament un arxiu de text. Creeu un arxiu anomenta parlar, li doneu permís d'execució i hi copieu això a dins:

#!/bin/sh
#parlar()
#El text a parlar ha d'anar entre dobles cometes, si no, tan sols llegeix la primera paraula."
#S'ha de posar l'arxiu on tingueu els vostres scripts  donant-li permisos amb sudo chmod +x
{
   echo "${1}" > /home/$USER/.textallegir
   festival --tts --language catalan /home/$USER/.textallegir
   rm /home/$USER/.textallegir
}

---

### Post by ciberado on 2010-11-29
Hola companys, em podeu dir si ja està disponible? o potser podria baixar directament els .deb pel Maverick?

Moltes gràcies.

jv

> **zeehio said:**
> Entre demà i demà passat em posaré a treballar per treure els paquets per Maverick.

No he pogut fer-ho abans.

Si voleu actualitzar i seguir utilitzant les veus catalanes, podeu fer servir el repositori de Lucid probablement i forçar la versió a la del repositori de FestCat.

Disculpeu el retard.

---

### Post by Darent on 2010-11-29
Hola, jo he provat a baixar-me els paquets manualment des del servidor per a Lucid i instal·lar-los amb sudo dpkg -i *.deb
S'instal·la tot sense cap error però després el programa al executar-lo i provar la veu en català em diu:

"Unsupported language, using English"
SIOD ERROR: unbound variable : voice_rab_diphone
festival: fatal error exiting.

... i ni tan sols funciona (vull dir, no s'escolta la veu en anglés ni en cap llengua)

També he provat a afegir el repositori per a lucid (estic a maverick) i instal·lar-ho per synaptic... mateix resultat.

EDITE:

Se m'oblidava, per si vols provar-ho els paquets me'ls vaig baixar d'aci:

[http://ppa.launchpad.net/zeehio/festcat/ubuntu/](http://ppa.launchpad.net/zeehio/festcat/ubuntu/)

> /pool/main/ (etcetera...)

Sort

Si tu tens més sort, si us plau, explica aci com ho has fet anar.

Salut

---

### Post by tjuanico on 2011-06-10
Bon dia:
 
Tinc un problema a veure si em podeu ajudar. Quan vull instal·lar les veus catalanes amb Ubuntu 10.10 (maverick meerkat) obtinc l'error següent. Ho he provat tant amb els paquets per la *lucid* com *yaunti*:
 
~$ echo "Bon dia" | festival --tts --> (veu anglesa per defecte, ok)
~$ echo "Bon dia" | festival --tts --language catalan
[COLOR=red]**SIOD ERROR: unbound variable : is_utf8 **[/COLOR]
 
vaig canviar el fitxer de festival *languages.scm* per tenir-ho així:
 
...
(define (language_catalan)
"(language_catalan)
Set up language parameter for catalan."
(set! female1 (lambda() (voice_upc_ca_ona_hts)))
(set! male1 (lambda() (voice_upc_ca_pau_hts)))
 
[COLOR=red]**(female1)**[/COLOR]
[COLOR=black](Param.set 'Language 'catalan)[/COLOR]
 
)
...
 
Quan introdueixo l'intrucció en vermell obtinc l'error, d'altra manera no, però obtinc la veu per defecte (anglesa) i no la catalana.
 
Faig alguna cosa malament? O és que he d'esperar a la distribució per Ubuntu 10.10 maverick? Quin és el problema: les distros tenen intèrprets de lisp diferents?
 
Gràcies i salutacions

---

### Post by friviere01 on 2011-06-13
Hola tjuanico,

Aquí tens instruccions detallades : [https://wiki.ubuntu.com/CatalanTeam/Tutorials/S%C3%ADntesiDeVeu]("https://wiki.ubuntu.com/CatalanTeam/Tutorials/S%C3%ADntesiDeVeu") i un apartat específic sobre el prolema que indiques.

Espero que et siguin d'alguna ajuda

(Edito) En tot cas sembla que el teu text es unicode (is_utf8) i recorda que el festival només funciona amb latin-1. Tot i qu em sembla que hi ha una versió catalana (festival-ca) que admet unicode: [https://launchpad.net/~zeehio/+ppa-packages]("https://launchpad.net/~zeehio/+ppa-packages"). Em penso que el primer enllaç també en parla.

---

### Post by zeehio on 2011-08-27
Per fi, he pogut treure noves veus i les he posat al repositori de sempre, per Maverick, Natty i Oneiric.

També he agafat els scripts del [tutorial]("https://wiki.ubuntu.com/CatalanTeam/Tutorials/S%C3%ADntesiDeVeu") i altres scripts que tenia desats i els he ordenat una mica i empaquetat en "festcat-utils".

[SIZE="4"]**Scripts i programes:**[/SIZE]
[LIST]
[*]audiollibre: Separa un fitxer de text en capítols i per cada capítol crea un fitxer d'àudio.
[*]    festcat: Interfície gràfica (cutre) als altres scripts.
[*]    festcat_llegeix: Llegeix un fitxer de text en veu alta.
[*]    readclipboard: Llegeix el contingut del portarretalls.
[*]    text2audio: Converteix un fitxer de text en àudio.
[/LIST]

A més instal·la tres programes més, que no estan pensats per l'usuari final, tot i que potser algú els usa:

[LIST]
[*]festcat_hts_engine: hts_engine és un motor per sintetitzar fitxers d'etiquetes. L'he adaptat perquè en faci moltes de cop.
[*]    festcat_text2wave: Com el text2wave, però permet més formats d'àudio (els de la eina sox), menja un 25% menys de CPU en veus HTS i no té el problema de menjar molta RAM al final (text2wave falla molt amb texts llargs).
[*]    divcapítols: Per separar un fitxer de text (llibre) en els seus diferents capítols.
[/LIST]

Tots els scripts venen amb una petita ajuda ($ man audiollibre)

He reescrit la majoria dels scripts per tal de fer servir funcions comunes a tots.
**[SIZE="4"]Característiques:[/SIZE]**
[LIST]
[*]Arguments de l'estil «audiollibre -a autor -v "upc_ca_ona_hts" llibre.txt» (ordre arbitrari, etc)
[*]    Detecció del fitxer de text pel contingut i no per l'extensió (no cal que siguin .txt, cal que continguin text).
[*]    Detecció de UTF-8 automàtica  i conversió si cal a ISO-8859-15.
[*]    Fa ús de l'eina "sox" per convertir l'àudio a moltíssims formats (depèn de què estigui instal·lat)
[*]    Neteja de caràcters problemàtics com á, ì o ù que no existeixen en català.
[*]    Interfície gràfica (cutre) disponible a: Aplicacions / Accés Universal / FestCat
[*]    Al crear fitxers d'àudio de texts llargs, utilitza molta menys memòria que text2wave i, si la veu és HTS, triga un 25% menys que text2wave.
[/LIST]

[B][SIZE="4"]
Instal·lació del repositori (Lucid o més nou):[/SIZE][/B]
```
sudo add-apt-repository ppa:zeehio/festcat
sudo apt-get update
```
Instal·lació de les veus:
```
sudo apt-get install festival-ca festvox-ca-upc-ona-hts festcat-utils 
```

**[SIZE="4"]Recomanacions[/SIZE]** (només si feu servir el repositori):
El mòdul d'àudio recomanat és:
(Param.set 'Audio_Method 'linux16audio)
El podeu posar al final del fitxer /etc/festival.scm amb l'ordre:
```
echo "(Param.set 'Audio_Method 'linux16audio)" | sudo tee -a /etc/festival.scm
```

Per **triar una veu** i usar-la als scripts, ho podeu fer així:
Aplicacions / Accés Universal / FestCat  i triar la opció "Canvia la veu"


**[SIZE="4"]Guia ràpida:[/SIZE]**
```

sudo add-apt-repository ppa:zeehio/festcat
sudo apt-get update
sudo apt-get install festival-ca festvox-ca-upc-ona-hts festcat-utils
echo "(Param.set 'Audio_Method 'linux16audio)" | sudo tee -a /etc/festival.scm

```
i ja pots usar: **Aplicacions / Accés Universal / FestCat**

Dels problemes coneguts del [tutorial]("https://wiki.ubuntu.com/CatalanTeam/Tutorials/S%C3%ADntesiDeVeu").
**Resolts**:
[LIST]
[*]Sintetitzar 2 admiracions seguides "!!" **No m'ha fallat**.
[*]Problema si la frase comença amb I majúscula. **No m'ha fallat**
[*]Llegir: TamTam i Pel·lícula **Funciona**
[*]UTF-8: **Funciona** (festcat-utils).
[*]Problemes d'àudio: **Resolt** amb linux16audio.
[/LIST]
**Pendents**
[LIST]
[*] Lectura de llistes (fer bé pauses).
[*] Pronunciar paraules amb caràcters estrangers.
[*] Associar readclipboard a una tecla al instal·lar festcat-utils. (sé fer-ho a gnome2, però no a gnome3, unity o kde)
[/LIST]

**[SIZE="4"]Exemples:[/SIZE]**
[LIST]
[*]
```
Sel·lecciona aquest text
```
Ara executa "readclipboard" a la consola.
[*] Executa: ```
 festcat_llegeix /usr/share/festival/upc_catalan/cat_intro.text 
```
[/LIST]

Probablement trobeu errors. Estaré pendent i els resoldré tan ràpid com em sigui possible.

Salut.

---

### Post by Darent on 2011-08-28
Genial, moltes gràcies per la feina!

Feia mesos que no aconseguia fer-lo anar, ni idea de per què (supose que el tenir els paquets de maverick instal·lats a natty).

Encara no em va perfecte (es bota les vocals amb accent) però crec que això és cosa del format de text, que ha de ser utf8 pel que tinc entés... si ho averigue ja ho posaré aci.

L'script que utilitze per llegir des de l'entrada d'ordres es diu "parlar" i conté això:

```
#!/bin/sh
#parlar()
#El text a parlar ha d'anar entre dobles cometes, si no, tan sols llegeix la primera paraula."
#S'ha de posar l'arxiu en $HOME/.scripts  donant-li permisos amb chmod +x i fent que .scripts estiga al $PATH
{
   echo "${1}" > $HOME/.textallegir
   festival --tts --language catalan $HOME/.textallegir
   rm $HOME/.textallegir
}
```

Per si a algú li serveix, o si saps com modificar-lo per que funcione amb els accents.

Gràcies de nou!

---

### Post by zeehio on 2011-09-01
@Darent, Festival no accepta UTF-8 (la manera de codificar accents més habitual actualment) correctament. Et dóno dues opcions:

[SIZE="3"]OPCIÓ MENYS BONA:[/SIZE]
Parxejar el "parlar" (tot i que encara podries trobar algun problema amb lletres com á, ì o ù que no existeixen en català). Aquesta opció requereix "iconv" del paquet libc-bin:
```
#!/bin/sh
#parlar()
#El text a parlar ha d'anar entre dobles cometes, si no, tan sols llegeix la primera paraula."
#S'ha de posar l'arxiu en $HOME/.scripts  donant-li permisos amb chmod +x i fent que .scripts estiga al $PATH
{
   echo "${1}" | iconv -f UTF-8 -t ISO-8859-15//IGNORE//TRANSLIT > $HOME/.textallegir
   festival --tts --language catalan $HOME/.textallegir
   rm $HOME/.textallegir
}
```

[SIZE="3"]OPCIÓ BONA:[/SIZE]
Instal·la el paquet festcat-utils (també en el repositori) i canvia la funció parlar per:
```

parlar () {
echo "${1}" | festcat_llegeix
}

```
Aquesta manera deixa en mans de festcat_llegeix el tema de codificar els accents correctament. Si trobes errors, envia'm el text que et dóna problemes i ho arreglaré quan pugui.


[SIZE="3"]OPCIÓ BONA 2[/SIZE]
```
sudo apt-get install festcat-utils
```
I fer a la terminal directament:
```
festcat_llegeix <<< "Hola amics d'aquest món"
```
i també:
```
festcat_llegeix "fitxer.txt"
```

[SIZE="3"]Opció arriscada[/SIZE]
Si no t'agrada el terminal també pots fer clic sobre un fitxer de text amb el botó dret i obrir-lo amb "/usr/bin/festcat_llegeix". **No tindràs manera d'aturar la lectura** (a part d'obrir un terminal i fer "pkill festival") o sigui que vigila, pot quedar-se xerrant molta estona!.

Més endavant (tot i que no prometo gaire) intentaré fer alguna aplicació gràfica més maca, o buscar com integrar festcat_llegeix amb l'Orca (el lector de pantalla de Gnome).

---

### Post by Darent on 2011-09-01
Hola, i gràcies per la resposta.

La veritat és que millor deixe estar això del meu script que és una cutrada, i ja que te'ls has currat utilitzaré el festival_llegeix amb combinacions de | o >>  (tenia ja instal·lat el festcat-utils però no l'havia provat). La idea que porte és que l'ordinador m'avise quan hi hagen alguns events (torrent abaixat, la cpu està a punt d'eixir en flames... etc).

He fet unes quantes  proves i ja em llegeix els accents oberts correctament, introduïnt el text i partint d'un arxiu de text. Si sortira algo ja ho deixaré aci. Per si et serveix d'algo, et diré que abans el que feia era llegir les paraules amb accents lletra a lletra.

Una última pregunta... quina diferència hi ha entre les veus hts i clunits? Pel que veig les clunits tenen molt més tamany, és per més definició? També ho pregunte perquè crec que aquestes no estan per a natty (les veig al repositori per http però al synaptic no m'apareixen).

De nou, gràcies per la feina. Mostrar-los el programa a amics "windowsers" els fa quedar-se al·lucinats... xD

---

### Post by zeehio on 2011-09-02
> **Darent said:**
> Hola, i gràcies per la resposta.

La veritat és que millor deixe estar això del meu script que és una cutrada, i ja que te'ls has currat utilitzaré el festival_llegeix amb combinacions de | o >>  (tenia ja instal·lat el festcat-utils però no l'havia provat). La idea que porte és que l'ordinador m'avise quan hi hagen alguns events (torrent abaixat, la cpu està a punt d'eixir en flames... etc).

Jo tinc un problema amb la targeta gràfica, i tinc un avís quan passa d'una temperatura màxima. Ho faig servir amb el "GNOME Sensors Applet" i va bé :).
> **Darent said:**
> 
He fet unes quantes  proves i ja em llegeix els accents oberts correctament, introduïnt el text i partint d'un arxiu de text. Si sortira algo ja ho deixaré aci. Per si et serveix d'algo, et diré que abans el que feia era llegir les paraules amb accents lletra a lletra.

He vist que falla al convertir el caràcter "&#320;" (ela geminada). Ho arreglaré quan tingui una estona.
> **Darent said:**
> 
Una última pregunta... quina diferència hi ha entre les veus hts i clunits? Pel que veig les clunits tenen molt més tamany, és per més definició? També ho pregunte perquè crec que aquestes no estan per a natty (les veig al repositori per http però al synaptic no m'apareixen).

Són dues tecnologies diferents:
Les veus clunits es basen en trossejar les gravacions originals marcant on comença cada fonema i crear una base de dades per posteriorment triar el tros d'àudio més adient en cada cas (en funció del context, de si és principi o final de paraula, principi o final de frase...).

Les veus hts es basen en entrenar uns models estadístics per cada fonema partint de les gravacions originals per, a l'hora de parlar, sintetitzar la veu a partir d'aquests models.

Les veus clunits necessiten d'una base de dades més gran que les hts, per tenir mostres representatives de tots els fonemes en tots els contextos. Això dóna lloc a que tinguin molt bona qualitat en algunes frases (si la frase està ben representada a la base de dades) però quan es pronuncia alguna paraula que no està ben representada a la base de dades l'error es nota molt més i és més molest.

Les veus hts són molt més lleugeres (no cal disposar de l'àudio, només dels models creats) i són molt més estables (poden sonar millor o pitjor, però en general no tenen errors greus).

He de revisar les veus clunits per assegurar-me que funcionen bé amb el nou festival i tot plegat. Quan ho hagi fet potser poso algunes al repositori. Tanmateix, l'espai del repositori és limitat, i el meu temps per mantenir les veus també ho és, de manera que ja veurem quantes veus acabo posant.

> **Darent said:**
> 
De nou, gràcies per la feina. Mostrar-los el programa a amics "windowsers" els fa quedar-se al·lucinats... xD
De res, m'alegra molt saber que les veus s'utilitzen!

Finalment, estic pendent de trobar un mentor a Debian (un Debian developer) que vulgui aprovar els meus paquets al repositori oficial: 
[http://mentors.debian.net/package/festival-ca](http://mentors.debian.net/package/festival-ca)
[http://mentors.debian.net/package/festvox-ca-ona-hts](http://mentors.debian.net/package/festvox-ca-ona-hts)
Si sabeu d'algú, comenteu-li. Un cop el paquet arribi a Debian podré fer un sync amb Ubuntu i altres distribucions, de manera que caurà al repositori oficial automàticament.

---

### Post by Darent on 2012-05-02
Hola de nou. Altra vegada amb problemes... Quan intente córrer festival  per la terminal, qualsevol de les seues funcions i inclús les veus en  anglés reb aquest missatge:

[HTML]darent@helena:~$ festcat_llegeix Documents/textos/Poema_Fremen.txt 
MacOS X audio support not compiled.
[/HTML]

Alguna idea de quin és el problema? Vaig estar eliminant algunes  llibreries que després d'actualitzar a precise em deia que estaven  obsoletes. Però  ni idea de quina llibreria d'àudio hauré esborrat, si  eixe és el cas.

Gràcies!

---

### Post by zeehio on 2012-05-02
Si em respons això et podré resoldre el problema més ràpidament:

De quina versió venies? (Lucid, Oneiric o una altra)

Quina versió de festival tens instal·lada?
al terminal:
```
$ dpkg-query -s festival | grep "Version"
```
i per últim al terminal:
```

$ festival
festival> (Param.get 'Audio_Method )

```


Nota: Per copiar coses del terminal pots sel·leccionar i apretar "Ctrl+majúscules+C" (en comptes del típic "Ctrl+C") o pots fer servir el menú Edita/Copia.

Moltes gràcies i disculpa les molèsties.

---

### Post by Darent on 2012-05-02
Vaja, això és ser ràpid :)

Vaig actualitzar d'oneiric a precise, i després vaig anar habilitant tots els ppa per precise que hi havien disponibles, inclòs el teu ppa. Tot funcionava bé però crec que el problema va venir en posar-me a esborrar lib* en la secció del synaptic "locals o obsolets". Només ho vaig fer amb les que no es carregava cap altre paquet, és a dir que creia que no causaven problemes de dependències. Ahi va ser quan va deixar de funcionar. He provat a reinstal·lar tot allò relacionat amb festival, tant el general com els paquets del teu repositori per veure si es tornaven a abaixar la dependència, i res.

dpkg-query -s festival | grep "Version"
Version: 1:2.1~release-4~ppa1


festival> festival> (Param.get 'Audio_Method )
SIOD ERROR: unbound variable : festival>

És un poc estrany, ni tan sols sé què té a veure mac os x amb l'ubuntu xD

Gràcies a tu, per la feina i per l'ajut!

---

### Post by Darent on 2012-05-02
Perdó, he executat mal la segona ordre. És:

festival> (Param.get 'Audio_Method )
"linux16audio"

---

### Post by zeehio on 2012-05-02
Sembla que és un problema de configuració, que al actualitzar no ho ha fet correctament (probablement culpa meva, però faig el que puc #-o )

Pots comprovar si al final del fitxer /etc/festival.scm hi ha escrit:
```

;; Debian-specific: Use aplay to play audio
(Parameter.set 'Audio_Command "aplay -q -c 1 -t raw -f s16 -r $SR $FILE")
(Parameter.set 'Audio_Method 'Audio_Command)

```
*NOTA*: Comprova que les línies Parameter.set NO comencen amb un ";".


A més, al terminal fes:
```
 cat ~/.festivalrc 
```
i si surt algun resultat me'l poses (el més probable és que digui "fitxer no trobat" o una cosa similar.

M'agradaria trobar la causa definitiva del problema. Tanmateix si escrius el següent al terminal s'hauria de solucionar:
```

echo << EOF
;; Debian-specific: Use aplay to play audio
(Param.set 'Audio_Command "aplay -q -c 1 -t raw -f s16 -r $SR $FILE")
(Param.set 'Audio_Method 'Audio_Command)
EOF >> ~/.festivalrc

```

---

### Post by Darent on 2012-05-02
Moltes gràcies, crec que ho he solucionat:

El arxiu /etc/festival.smc contenia això:

;; Debian-specific: Use aplay to play audio
(Parameter.set 'Audio_Command "aplay -q -c 1 -t raw -f s16 -r $SR $FILE")
(Parameter.set 'Audio_Method 'Audio_Command)
(Param.set 'Audio_Method 'linux16audio)
(Param.set 'Audio_Method 'linux16audio)
(Param.set 'Audio_Method 'linux16audio)
(Param.set 'Audio_Method 'linux16audio)

Quan ho he vist he recordat que dies enrere vaig executar una ordre per a introduïr eixa darrera línia a l'arxiu (algo de l'estil:
 sudo echo "(Param.set 'Audio_Method 'linux16audio)" >> /etc/festival.smc
... o quelcom semblant.

Sento no recordar a quin fòrum ho vaig veure... I el cas és que la línia està repetida perquè pel que es veu vaig repetir l'ordre vàries vegades. Sent no  haver-ho pogut mencionar primer perquè t'hauria estalviat un mal de cap.

El cas és que he esborrat eixes quatre línies i ho he deixat tal com dius al teu comentari:

;; Debian-specific: Use aplay to play audio
(Parameter.set 'Audio_Command "aplay -q -c 1 -t raw -f s16 -r $SR $FILE")
(Parameter.set 'Audio_Method 'Audio_Command)
 
En quan a l'arxiu .festivalrc no existeix, però tot ha començat a funcionar bé. Si ho entenc bé, /etc/festival.smc seria com una configuració global, i el .festivalrc és la configuració personalitzada al meu directori d'usuari. Per si de cas he creat l'arxiu amb el contingut de dalt.

Ara tot torna a anar, l'únic que dóna problemes és el menú amb zenity de festcat. Apareix, però en triar qualsevol opció i prémer acceptar es tanca i no fa res. Però això crec que és un problema amb zenity o amb el theme que estic utilitzant. Amés estic utilitzant gnome-session-fallback amb compiz i algunes aplicacions gràfiques no responen massa bé. De totes formes el festival per línia d'ordres ja em va bé per posar-lo a algun script.

Moltes gràcies per l'ajuda i per tota la feina que estàs fent! :)

---

### Post by zeehio on 2012-05-02
Molt ben fet. 

Pel que fa el menú, es un error de zenity:
[https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/968534](https://bugs.launchpad.net/ubuntu/+source/zenity/+bug/968534)
Esta resolt. Nomes falta que algú d'ubuntu faci l'actualitzacio. 

Pel tema del linux16audio que tenies escrit, el mòdul de festival per reproduir so a Linux te problemes i cal algú que sàpiga com funciona ALSA (sistema de so a Linux) per arreglar-los. 
Jo mateix vaig intentar-ho però no en se prou. 

Els mantenidors de festival a Debian hi estan treballant però tampoc son experts en ALSA. 

Fins la propera :-)

---

### Post by Darent on 2012-05-03
Bé, doncs arreglat, gràcies per l'ajuda. M'he subscrit a l'informe d'error, tota pedra fa paret xD
Fins a l'altra que torne a ficar la pota, no hauria de jugar tant amb els ppa's...

Salut!

---

### Post by Darent on 2012-05-03
Bé, doncs arreglat, gràcies per l'ajuda. M'he subscrit a l'informe d'error, tota pedra fa paret xD
Fins a l'altra que torne a ficar la pota, no hauria de jugar tant amb els ppa's...

Salut!

---

### Post by zeehio on 2012-05-12
> **Darent said:**
> Bé, doncs arreglat, gràcies per l'ajuda. M'he subscrit a l'informe d'error, tota pedra fa paret xD
Fins a l'altra que torne a ficar la pota, no hauria de jugar tant amb els ppa's...

Salut!

Crec que el bug de zenity està resolt.
Aplicant les darreres actualitzacions puc utilitzar festcat com sempre.

---

### Post by Darent on 2012-10-24
Mmmm em sent mal de ja preguntar-te la mateixa cosa cada sis mesos, però... tens pensat fer un repository per a quantal? Gràcies per la feina com sempre, salut! :)

---

### Post by zeehio on 2012-10-24
> **Darent said:**
> Mmmm em sent mal de ja preguntar-te la mateixa cosa cada sis mesos, però... tens pensat fer un repository per a quantal? Gràcies per la feina com sempre, salut! :)

Pitjor em sento jo de no haver-ho fet abans! :-)

Gràcies pel recordatori. He copiat els paquets necessaris de precise que haurien de funcionar sense problemes. Tanmateix  ara no tinc temps per provar-ho perquè no tinc cap quantal en marxa. :-S

Si et trobessis cap problema (que no ho crec), no dubtis en escriure i miraré de resoldre-ho tan ràpid com pugui. 

Disculpa les molèsties i gràcies!

---

### Post by Darent on 2012-11-22
Doncs m'apareix aquest error de dependències:

No s'han trobat les dependències del paquets següents:
 festival-ca : Depèn: festival (>= 1:2.1~release-3) però el 1:2.1~release-1ubuntu3 està instal·lat.
Les accions següents resoldran les dependències:

     Mantín la versió actual dels següents paquets:
1)     festival-ca [No instal·lat]

Primer pensava que s'arreglaria amb alguna actualització, però no és el cas. Sembla ser que el release-1 el considera més antic que release-3 i no deixa instal·lar festival-ca ni tampoc si prove a instal·lar la veu d'Ona.

Sento no haver contestat abans, no sé per què no reb avisos d'aquest fil.

Gràcies!

---

### Post by zeehio on 2012-11-26
> **Darent said:**
> Doncs m'apareix aquest error de dependències:

No s'han trobat les dependències del paquets següents:
 festival-ca : Depèn: festival (>= 1:2.1~release-3) però el 1:2.1~release-1ubuntu3 està instal·lat.
Les accions següents resoldran les dependències:

     Mantín la versió actual dels següents paquets:
1)     festival-ca [No instal·lat]

Primer pensava que s'arreglaria amb alguna actualització, però no és el cas. Sembla ser que el release-1 el considera més antic que release-3 i no deixa instal·lar festival-ca ni tampoc si prove a instal·lar la veu d'Ona.

Sento no haver contestat abans, no sé per què no reb avisos d'aquest fil.

Gràcies!

Vaig llegir malament la versió de festival que venia amb quantal. On deia la release1-ubuntu3 vaig llegir release3-ubuntu1.

He pujat una versió més nova de festival que us hauria d'aparèixer com a actualització. No tinc quantal, però us hauria de funcionar.

Disculpeu les molèsties.

---

### Post by Darent on 2012-12-14
Arreglat, i funcionant  perfectament. Gràcies de nou!

P.D. No sé per què no tinc avisos de  nous posts a aquests fòrums, per això he tardat en contestar. Salut!

---

