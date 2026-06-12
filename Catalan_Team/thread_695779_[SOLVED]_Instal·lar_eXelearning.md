---
title: "[SOLVED] Instal·lar eXelearning"
date: 2008-02-13
forum: Catalan Team
---

### Post by ipelegri6 on 2008-02-13
Hola,

Sóc completament novata en linux i en kubuntu, però decidida a abandonar windows m'hi he llançat i ara no tinc més remei que aprendre'n.
La cosa és que estic intentant instal·lar eXelearning i finalment he trobat una pàgina que explica com fer-ho: [http://www.iesgabrielciscar.org/eXe/index.html](http://www.iesgabrielciscar.org/eXe/index.html)

Segueixo totes les passes (he aconseguit desar el fitxer python2.5-exe_1.03.0.3373-ubuntu1_i386.deb dins el directori /usr/bin/eXe/) però la instal·lació falla. El missatge que surt a la consola és:
-------------------------------------
root@PELEGRI:/usr/bin/eXe# sudo dpkg -i python2.5-exe_1.03.0.3373-ubuntu1_i386.deb
(S'està llegint la base de dades ... hi ha 126681 fitxers i directoris instal·lats actualment.)
S'està desempaquetant python2.5-exe (de python2.5-exe_1.03.0.3373-ubuntu1_i386.deb) ...
dpkg: s'ha produït un error en processar python2.5-exe_1.03.0.3373-ubuntu1_i386.deb (--install):
 s'està intentant sobreescriure «/usr/bin/run-exe.sh», que també està en el paquet python2.4-exe
dpkg-deb: el subprocés paste fou finalitzat pel senyal (Broken pipe)
S'han trobat errors en processar:
 python2.5-exe_1.03.0.3373-ubuntu1_i386.deb
-----------------------------------------

Bé, no hi entenc res de res, però per si de cas he reanomenat el fitxer run-exe.sh a run-exe-vell.sh i ho he tornat a intentar. I surt el mateix.

Tins més problemes (amb secondlife, amb el java,...) però amb l'ajut de bons amics (i espero que també aquest fòrum) me'n sortiré.

Espero haver escrit al lloc adequat!!!

Irene

---

### Post by papapep on 2008-02-13
Benvinguda Irene! (no oblidis passar pel fil de benvinguda ;) )

Doncs on coneixia l'eXelearning aquest, però sembla molt interessant!!

Respecte el teu problema, hauriem de comprovar que les passes que has fet han funcionat correctament fins arribar a aquest punt on ets ara del procés d'instal·lació. Fes, si us plau, a un terminal:

```
sudo aptitude search python-imaging python-zopeinterface
```

a més, estaria bé saber quina versió de Ubuntu fas servir i quin kernel tens instal·lat. Pel kernel:

```
uname -a
```

EDICIÓ: L'he instal·lat per provar, i m'ha funcionant perfectament. O sigui que no és problema del paquet de l'eXelearning.

---

### Post by lluisanunez on 2008-02-13
Irene, benvinguda a la comunitat Ubuntu!
La Irene és un membre molt actiu de la comunitat [Moodle]("http://moodle.org") :)
Estic seguint el tema de l'eXelearning per insta&#320;lar-me'l jo també...

---

### Post by ipelegri6 on 2008-02-14
je, je, ens tornem a trobar, Lluïsa :-)
Ara  són menys activa a moodle.org i més activa "a l'ombra": en aquests moments tinc uns 100 profes que estan aprenent a utilitzar moodle a diferents cursos!
Espero sortir-me'n amb l'exelearning i això que no funcioni a la primera em té més encuriosida encara...

---

### Post by ipelegri6 on 2008-02-14
Hola Josep,
Moltes gràcies per la teva resposta i per avisar-me que passi pel fil de benvinguda, ara hi vaig!

He fet el que m'has dit i han aparegut les següents lletres (encara no són missatges per a mi):
---------------------------

Password:
i   python-imaging                  - Python Imaging Library
p   python-imaging-dbg              - Python Imaging Library (debug extension)
p   python-imaging-doc              - Examples for the Python Imaging Library
p   python-imaging-doc-html         - Documentation for the Python Imaging Libr
p   python-imaging-doc-pdf          - Documentation for the Python Imaging Libr
p   python-imaging-sane             - Python Imaging Library - SANE interface
p   python-imaging-sane-dbg         - Python Imaging Library - SANE interface (
p   python-imaging-tk               - Python Imaging Library - ImageTk Module
p   python-imaging-tk-dbg           - Python Imaging Library - ImageTk Module (
i   python-zopeinterface            - The implementation of interface definitio
p   python-zopeinterface-dbg        - The implementation of interface definitio
irene@PELEGRI:~$ uname -a
Linux PELEGRI 2.6.20-16-generic #2 SMP Tue Feb 12 05:41:34 UTC 2008 i686 GNU/Linux
irene@PELEGRI:~$   
.---------------------------------------
 Pel que fa a la versió d'Ubuntu, pot ser kubuntu 7.04? No sé on buscar-la, però en clicar a ajuda m'ha sortit la d'aquesta versió. Per instal·lar el kubuntu l'únic que vaig fer va ser posar un CD que m'havia passat el coordinador d'informàtica de l'institut on treballo i a partir d'aquí tot va rodar autònomament.

M'anima saber que el programa funciona! Per cert, molt bona l'ajuda de l'interpret de comandes, segur que em serà útil, n'hi ha molt per aprendre! :-)

---

### Post by papapep on 2008-02-14
Doncs considerant que jo tinc la 7.10, potser seria bo que actualitzessis el sistema a aquesta última versió estable. Probablement tinguis un conflicte de versions amb algun d'aquest paquets que fa servir l'eXelearning (com que al manual d'instal·lació no parlen de versions, no ho podem saber segur).

---

### Post by ipelegri6 on 2008-02-14
Sí, cada vegada que instal·lo actualitzacions em diu que hi ha disponible una nova versió, però em fa una mica de por fer un canvi tan gran, ara que les eines principals em funcionen correctament. De totes maneres, si penses que pot ser això, ho provo. Ai, ai, ai...

---

### Post by papapep on 2008-02-14
:-D Doncs s'ha de valorar abans de fer el canvi. Quan dius "les eines principals", a què et refereixes en concret??

Pensa que tots, o gairebé, passem pel procés d'actualització i, excepte casos comptats i bastant concrets, no hi ha cap daltabaix.

---

### Post by ipelegri6 on 2008-02-14
D'acord, m'arriscaré.

Per a mi les eines principals són el firefox, el GIMP i l'openoffice, perquè gairebé tot ho faig a la xarxa. Sobretot el firefox, tot i que encara no li he acabat d'instal·lar tots els connectors, però estoy en ello.

Actualitzo i si no apareixo per aquí és que no ha funcionat...

---

### Post by SiscoGarcia on 2008-02-14
Hola Irene, benvinguda!

Si les eines principals són firefox, gimp i openoffice no has de patir perquè estan ben resoltes a la 7.10. Jo faig servir gnome (ubuntu) però vaig provar la kubuntu 7.10 en una màquina vella i em va funcionar sense cap problema. No pateixis, en qualsevol cas sempre et queda la tornada enrere ;)

---

### Post by telejet on 2008-02-14
Ei, moltes felicitats a tots, he descobert aquest fantàstic eXelearning, i la guia de [http://www.iesgabrielciscar.org/eXe/](http://www.iesgabrielciscar.org/eXe/) és molt complerta.

Avui l'he instal·lat al windows de la feina sense problema i a l'ubuntu 7.10 de casa i funciona perfectament. 

Veig que tu al fer la instal·lació ho fas com a root i baixant el deb a una carpeta del sistema, jo i molta altra gent no ho faria.

Entra com a usuari normal (amb drets de sudo) i fes primer

```
sudo apt-get install python-imaging python-zopeinterface
```

després com a usuari normal descarregat el paquet deb i el deses a l'escriptori (després ja el podràs esborrar si vols) i des d'allà amb un doble click ja l'obres amb el gdebi que t'instal·larà el paquet i llestos.

Vas a Aplicacions-accesoris-eXe i endavant

Tant t'ha de funcionar amb la 7.04 com amb la 7.10.

Reitero les meves felicitacions per la descoberta del programa, he fet bastantes coses amb moodle i actualment tinc la dona enfrascada amb el HotPotatoes (que vam tenir que còrrer amb wine ja que la versió java era molt limitada) i aquest ens anirà de perles.

Fins ara,

Ivan

---

### Post by ipelegri6 on 2008-02-14
Hola!
SiscoGarcia, com es fa per tornar enrere? La instal·lació no ha acabat: un fitxer de*** (no recordo com) deia que no es podia instal·lar, després tampoc ha pogut amb /var/cache/apt/archives/x11-common_1%3a7.2-5ubuntu13_i386.deb

ni tampoc x11-common.

He anat enviant els bugs i finalment s'ha quedat encallat més de mitja hora preparant libatk1.0-0, amb el 2% instal·lat.

M'ha dit que el sistema podia quedar inservibles i ara mateix a l'adept_updater hi ha disponibles 882 paquets actualitzats.

Em fa por apagar l'ordinador i no poder-lo engegar! (ara, de moment, funciona). Què faig? :confused:

Irene

---

### Post by ipelegri6 on 2008-02-14
Hola telejet,
De moment no goso fer-hi més coses, m'he quedat a mitja instal·lació.
Ei, jo treballo amb el hotpotatoes en java, N'hi ha un de millor???

M'esteu fent dentetes, i jo sense poder veure el programa!!!!!

---

### Post by lluisanunez on 2008-02-14
Irene, prova de fer un 
```
sudo apt-get clean
```

---

### Post by telejet on 2008-02-14
Hola Irene,

espero que solucionis els problemes d'actualització, per quan estiguis només comentar-te que el Hotpotatoes del java és la versió 6.0.2, però si el vols més complert tens el 6.2 que corre en windows i també en linux amb el WINE. 

És molt senzill d'instal·lar, primer el WINE

sudo apt-get install wine

després descarregues la carpeta comprimida [http://hotpot.uvic.ca/wine_hotpot62.zip](http://hotpot.uvic.ca/wine_hotpot62.zip) i la descomprimexes on tu vulguis (al teu directori d'usuari o al .wine/drive_c/Program Files

Per executar-lo vas a un terminal, et situes al directori on has ficat el Hotpotatoes i fas
wine HotPot.exe
Si ho vols més fàcil pots crear-te una llançadora que executi aquesta ordre.

No havia provat mai el WINE però va molt bé per aquells programes de windows que puguis necessitar puntualment

---

### Post by ipelegri6 on 2008-02-14
Moltes gràcies!!

Provaré el que comentes, Lluïsa. Puc trencar alguna cosa?
Em sembla que ho deixo per demà, per avui ja he tingut prou ensurts...

---

### Post by papapep on 2008-02-14
> La instal·lació no ha acabat: un fitxer de*** (no recordo com) deia que no es podia instal·lar

Irene, per a poder-te ajudar en condicions, cal que sapiguem què has fet exactament (quina ordre exacta has executat) i quin missatge en concret rebs. Sinó no tenim base per a poder valorar cap a on tirar.

De fet que un paquet no s'instal·li no significa problemes de manera directa. Depèn de quin paquet sigui.

> He anat enviant els bugs

A què et refereixes amb "he anat enviant"?? a on els envies??

En situacions d'aquestes, el primer que s'ha de fer és "parar el carro" i mirar-se les coses amb tranquilitat. Anem a intentar trobar la font del teu problema.

PD Per si no ho has fet abans, aquest és un bon moment per fer una còpia en CD/DVD dels fitxers que consideris importants. Mai està de més.

---

### Post by SiscoGarcia on 2008-02-14
Amb "tornar enrere" el que volia dir-te és que sempre tens la possibilitat d'instal·lar la versió anterior, ni que no sigui gens "elegant". De tota manera, no pateixis, segurament es podrà arreglar si vas dient què és el que ha passat cronològicament.

De vegades els ensurts ens els imaginem més greus del que realment són degut a la nostra ignorància.;)

---

### Post by ipelegri6 on 2008-02-15
Hola papapep,

El primer fitxer no recordo el nom perquè em pensava que havia copiat el missatge d'error on em deia el  nom del fitxer però em vaig equivocar. Als altres dos ja em vaig assegurar.,,
Enviar els bugs és perquè cada vegada que em deia que no podia instal·lar un fitxer em demanava si volia enviar el bug i jo li deia que sí. Pensava una estona (no jo, el programa) i ja està. No em donava cap missatge de confirmació "bug enviat". Suposo que el que fa és trametre el bug de la instal·lació a l'equip que les fa, no?

Aturar: de fet, ja vaig aturar l'actualització i de moment no ha passat res greu, tot sembla funcionar correctament. 

Abans de fer res més passaré tots els fitxers importants a un disc dur extern. Fins dilluns no tornaré a tenir ordinador, així que de moment ho deixo.

SiscoGarcia, tens raó, que sembla més gran quan no sabem de què va. Amv l'XP ja vaig haver de formatejar el disc dur i tornar a fer la instal·lació unes quantes vegades, o sigui que per això ja estic preparada :-)

Irene

---

### Post by papapep on 2008-02-15
> Aturar: de fet, ja vaig aturar l'actualització i de moment no ha passat res greu, tot sembla funcionar correctament. 

Uiiiiii, això si que no s'ha de fer..... Aquesta és una de les situacions que et podria haver portat molts problemes (vaja, provocar que haguessis de reinstal·lar de cero). Però si arrenca normalment, ho hauràs fet en un moment "no crític". Però per a propers cops, millor no fer-ho :-)

D'acord Irene, quan tinguis l'ordinador un altre cop seguirem investigant com està el malalt ;-)

---

### Post by ipelegri6 on 2008-02-20
Hola,
Han passat uns dies però he estat traslladant de servidor dos cursos de moodle, amb els seus corresponents participants i cursos de pràctiques. Sembla que tot fa crashhh, darrerament!
On m'havia quedat? Intentant actualitzar a la 7.10, que no he pogut. Llavors vaig fer 
sudo apt-get clean

com em vas aconsellar, Lluïsa.

Vaig haver d'aturar perquè l'actualització s'havia quedat completament bloquejada.

Com esti ara? M'he quedat sense openoffice (ara treballo a googledocs) i no puc accedir a l'instal·lador Adept ni a Synaptic perquè em diuen que:

"Un altre procés està utilitzant la base de dades del sistema de paquets (probablement alguna altra aplicació Adept o l'apt-get o l'aptitude). Tanqueu l'altra aplicació abans d'utilitzar aquesta."

També tinc un senyal d'alerta a la barra inferior que em diu que tind 882 paquets actualitzats però quan intento entrar em surt el mateix missatge anterior.

De moment, però, firefox, hotpotatoes en java i gimp funcionen. Secondlife i eXe no. I vaig poder desar els fitxers a un disc dur extern.

Quan tingueu un momentet lliure... què faig?

Irene

---

### Post by papapep on 2008-02-20
L'apt-get clean es va quedar bloquejat? Això no és una actualització de paquets, només fa neteja dels .deb que ha baixat a fi de deixar lliure espai innecessari.

Intentem atacar el tema amb racionalitat:

Abans que res, atura i reinicia el teu ordinador (si, ja sé que això és tipic de windows, però a vegades cal fer-ho :-D).

Un cop fet això, fes a un terminal:

```
sudo apt-get -f install
```

i enganxa aquí el que et respongui la màquina (per llarg que sigui)

---

### Post by ipelegri6 on 2008-02-20
Doncs m'ha donat un missatge molt curt:

irene@PELEGRI:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by papapep on 2008-02-20
Molt bé, doncs ara fes el que diu:

```
sudo dpkg --configure -a
```

---

### Post by ipelegri6 on 2008-02-20
Ei, ara sí que m'ha donat un munt de text per copiar :-)

irene@PELEGRI:~$ sudo dpkg --configure -a
S'està configurant debconf (1.5.14ubuntu1) ...

S'està configurant libart-2.0-2 (2.3.19-3) ...

dpkg: problemes de dependències impedeixen la configuració de kipi-plugins:
 kipi-plugins depèn de kdelibs4c2a (>= 4:3.5.7-1); tot i així:
  La versió del paquet «kdelibs4c2a» al sistema és 4:3.5.6-0ubuntu14.2.
 kipi-plugins depèn de libgphoto2-2 (>= 2.3.1); tot i així:
  La versió del paquet «libgphoto2-2» al sistema és 2.3.0-0ubuntu4.
 kipi-plugins depèn de libgphoto2-port0 (>= 2.3.1); tot i així:
  La versió del paquet «libgphoto2-port0» al sistema és 2.3.0-0ubuntu4.
 kipi-plugins depèn de libgpod2; tot i així:
  El paquet libgpod2 no està instal·lat.
 kipi-plugins depèn de libkcal2b (>= 4:3.5.7); tot i així:
  La versió del paquet «libkcal2b» al sistema és 4:3.5.6-0ubuntu6.
 kipi-plugins depèn de libkdcraw1; tot i així:
  El paquet libkdcraw1 no està instal·lat.
 kipi-plugins depèn de libkexiv2-1; tot i així:
  El paquet libkexiv2-1 no està instal·lat.
 kipi-plugins depèn de libstdc++6 (>= 4.2-20070516); tot i així:
  La versió del paquet «libstdc++6» al sistema és 4.1.2-0ubuntu4.
 kipi-plugins depèn de libxml2 (>= 2.6.29); tot i així:
  La versió del paquet «libxml2» al sistema és 2.6.27.dfsg-1ubuntu3.1.
dpkg: s'ha produït un error en processar kipi-plugins (--configure):
 problemes de dependències - es deixa sense configurar
S'està configurant linux-libc-dev (2.6.22-14.52) ...
dpkg: problemes de dependències impedeixen la configuració de gwenview:
 gwenview depèn de kdelibs4c2a (>= 4:3.5.7-1); tot i així:
  La versió del paquet «kdelibs4c2a» al sistema és 4:3.5.6-0ubuntu14.2.
 gwenview depèn de libexiv2-0; tot i així:
  El paquet libexiv2-0 no està instal·lat.
 gwenview depèn de libstdc++6 (>= 4.2-20070516); tot i així:
  La versió del paquet «libstdc++6» al sistema és 4.1.2-0ubuntu4.
dpkg: s'ha produït un error en processar gwenview (--configure):
 problemes de dependències - es deixa sense configurar
S'està configurant libasound2 (1.0.14-1ubuntu8) ...
You may need to execute the asoundconf(1) set-default-card macro.

S'està configurant libperl5.8 (5.8.8-7ubuntu3.1) ...

S'està configurant libdb4.4 (4.4.20-8.1ubuntu3.1) ...
S'està configurant x11-common (7.2-0ubuntu11) ...

dpkg: problemes de dependències impedeixen la configuració de digikam:
 digikam depèn de kdelibs4c2a (>= 4:3.5.7-1); tot i així:
  La versió del paquet «kdelibs4c2a» al sistema és 4:3.5.6-0ubuntu14.2.
 digikam depèn de libexiv2-0; tot i així:
  El paquet libexiv2-0 no està instal·lat.
 digikam depèn de libfreetype6 (>= 2.3.5); tot i així:
  La versió del paquet «libfreetype6» al sistema és 2.2.1-5ubuntu1.1.
 digikam depèn de libgphoto2-2 (>= 2.4.0); tot i així:
  La versió del paquet «libgphoto2-2» al sistema és 2.3.0-0ubuntu4.
 digikam depèn de libgphoto2-port0 (>= 2.4.0); tot i així:
  La versió del paquet «libgphoto2-port0» al sistema és 2.3.0-0ubuntu4.
 digikam depèn de libjasper1 (>= 1.900.1); tot i així:
  El paquet libjasper1 no està instal·lat.
 digikam depèn de libkdcraw1; tot i així:
  El paquet libkdcraw1 no està instal·lat.
 digikam depèn de libkexiv2-1; tot i així:
  El paquet libkexiv2-1 no està instal·lat.
 digikam depèn de libsqlite3-0 (>= 3.4.2); tot i així:
  La versió del paquet «libsqlite3-0» al sistema és 3.3.13-0ubuntu1.
 digikam depèn de libstdc++6 (>= 4.2.1); tot i així:
  La versió del paquet «libstdc++6» al sistema és 4.1.2-0ubuntu4.
 digikam depèn de zlib1g (>= 1:1.2.3.3.dfsg-1); tot i així:
  La versió del paquet «zlib1g» al sistema és 1:1.2.3-13ubuntu4.
dpkg: s'ha produït un error en processar digikam (--configure):
 problemes de dependències - es deixa sense configurar
S'està configurant libgpmg1 (1.19.6-25) ...

S'està configurant libartsc0 (1.5.8-0ubuntu1) ...

S'està configurant libc6-i686 (2.6.1-1ubuntu10) ...

S'està configurant libice6 (1.0.3-3) ...

S'està configurant libx11-data (1.1.1-1ubuntu4) ...
S'està configurant libsm6 (1.0.3-1) ...

S'està configurant libglib2.0-0 (2.14.1-1ubuntu1) ...

S'està configurant libxau6 (1.0.3-2) ...

S'està configurant libxdmcp6 (1.0.2-2) ...

S'està configurant libc6-dev (2.6.1-1ubuntu10) ...
S'està configurant libx11-6 (1.1.1-1ubuntu4) ...

S'està configurant libaa1 (1.4p5-32) ...

S'està configurant libxt6 (1.0.5-3) ...

S'està configurant libaudio2 (1.9-2) ...

S'està configurant perl-modules (5.8.8-7ubuntu3.1) ...
S'està configurant perl (5.8.8-7ubuntu3.1) ...

S'està configurant perl-suid (5.8.8-7ubuntu3.1) ...
S'han trobat errors en processar:
 kipi-plugins
 gwenview
 digikam


(per cert, el gwenview tampoc em funcionava, però com que no sé per a què serveix no m'amoïnava)

I ara?

---

### Post by papapep on 2008-02-20
Bé, prova a fer ara el d'abans:

```
sudo apt-get -f install
```

Si funciona correctament, fes:

```
sudo aptitude update
```

i 

```
sudo aptitude safe-upgrade
```

---

### Post by ipelegri6 on 2008-02-20
T'envio tot el que m'ha dit?  És llarguíssim, i al final em diu que la meva aptitud no té superpoders bovins (però si sóc taure!!!)

En fi, m'ha sortit tot això:

irene@PELEGRI:~$ sudo apt-get -f install
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
S'estan corregint les dependències... Fet
The following packages were automatically installed and are no longer required:
  libenchant1c2a libgail18 libgail-common libgnome-menu2 libgtkhtml2-0
  mingw32-runtime mingw32-binutils
Use 'apt-get autoremove' to remove them.
S'instal·laran els següents paquets extres:
  gimp gimp-data kdelibs-data kdelibs4c2a libatk1.0-0 libcupsys2 libdbus-1-3
  libdbus-glib-1-2 libexiv2-0 libfreetype6 libgimp2.0 libgnutls13 libgphoto2-2
  libgphoto2-port0 libgpod2 libgsf-1-114 libgsf-1-common libgtk2.0-0
  libgtk2.0-common libhal1 libjasper1 libkcal2b libkdcraw1 libkdepim1a
  libkexiv2-1 libkeyutils1 libkrb53 libktnef1 liblzo2-2 libopencdk8
  libpango1.0-0 libpango1.0-common libpoppler-glib2 libpoppler2 librsvg2-2
  librsvg2-common libsqlite3-0 libstdc++6 libwmf0.2-7 libxdamage1 libxml2 zlib1g
Paquets suggerits:
  gimp-help-en gimp-help gimp-python libgimp-perl gimp-data-extras fam
  libfreetype6-dev gnutls-bin gphoto2 gtkam krb5-doc krb5-user ttf-thryomanes
  librsvg2-bin
Paquets recomanats:
  gimp-gnomevfs gimp-libcurl libatk1.0-data exiv2 libgpod-common
S'ELIMINARAN els següents paquets:
  gtk-qt-engine
S'instal·laran els següents paquets NOUS:
  libexiv2-0 libgpod2 libjasper1 libkdcraw1 libkexiv2-1 libkeyutils1 liblzo2-2
  libpoppler-glib2 libpoppler2
S'actualitzaran els següents paquets:
  gimp gimp-data kdelibs-data kdelibs4c2a libatk1.0-0 libcupsys2 libdbus-1-3
  libdbus-glib-1-2 libfreetype6 libgimp2.0 libgnutls13 libgphoto2-2
  libgphoto2-port0 libgsf-1-114 libgsf-1-common libgtk2.0-0 libgtk2.0-common
  libhal1 libkcal2b libkdepim1a libkrb53 libktnef1 libopencdk8 libpango1.0-0
  libpango1.0-common librsvg2-2 librsvg2-common libsqlite3-0 libstdc++6
  libwmf0.2-7 libxdamage1 libxml2 zlib1g
33 actualitzats, 9 nous a instal·lar, 1 a eliminar i 846 no actualitzats.
4 no instal·lats o eliminats completament.
Es necessita obtenir 34,2MB d'arxius.
Després de desempaquetar s'usaran 16,6MB d'espai en disc addicional.
Voleu continuar [S/n]? s
Des:1 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main liblzo2-2 2.02-3 [59,8kB]
Des:2 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main zlib1g 1:1.2.3.3.dfsg-5ubuntu2 [73,0kB]
Des:3 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libopencdk8 0.5.13-2 [101kB]
Des:4 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libgnutls13 1.6.3-1build1 [314kB]
Des:5 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libkeyutils1 1.2-3 [4960B]
Des:6 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libkrb53 1.6.dfsg.1-7build1 [462kB]
Des:7 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main libcupsys2 1.3.2-1ubuntu7.5 [182kB]
Des:8 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libfreetype6 2.3.5-1ubuntu4 [348kB]
Des:9 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libjasper1 1.900.1-3 [142kB]
Des:10 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libstdc++6 4.2.1-5ubuntu4 [315kB]
Des:11 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main libxml2 2.6.30.dfsg-2ubuntu1.1 [770kB]
Des:12 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main kdelibs4c2a 4:3.5.8-0ubuntu3.3 [10,0MB]
Des:13 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main kdelibs-data 4:3.5.8-0ubuntu3.3 [7295kB]
Des:14 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libexiv2-0 0.15-1ubuntu2 [346kB]
Des:15 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libdbus-1-3 1.1.1-3ubuntu4 [129kB]
Des:16 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libhal1 0.5.9.1-6ubuntu5 [371kB]
Des:17 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libgphoto2-port0 2.4.0-2ubuntu2 [94,8kB]
Des:18 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libgphoto2-2 2.4.0-2ubuntu2 [775kB]
Des:19 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libkdcraw1 0.1.1-2 [130kB]
Des:20 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libkexiv2-1 0.1.5-1ubuntu2 [66,2kB]
Des:21 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libsqlite3-0 3.4.2-1build1 [211kB]
Des:22 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libwmf0.2-7 0.2.8.4-6 [175kB]
Des:23 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libgtk2.0-common 2.12.0-1ubuntu3 [181kB]
Des:24 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libatk1.0-0 1.20.0-0ubuntu1 [79,1kB]
Des:25 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main libpango1.0-common 1.18.3-0ubuntu1 [63,5kB]
Des:26 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main libpango1.0-0 1.18.3-0ubuntu1 [293kB]
Des:27 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libxdamage1 1:1.1.1-3 [9794B]
Des:28 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libgtk2.0-0 2.12.0-1ubuntu3 [1964kB]
Des:29 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libgpod2 0.5.2-2 [181kB]
Des:30 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main libktnef1 4:3.5.7enterprise20070926-0ubuntu2.1 [61,4kB]
Des:31 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main libkdepim1a 4:3.5.7enterprise20070926-0ubuntu2.1 [604kB]
Des:32 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main libkcal2b 4:3.5.7enterprise20070926-0ubuntu2.1 [658kB]
Des:33 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main gimp-data 2.4.2-0ubuntu0.7.10.1 [1977kB]
Des:34 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main gimp 2.4.2-0ubuntu0.7.10.1 [3897kB]
Des:35 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libdbus-glib-1-2 0.74-1 [134kB]
Des:36 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main libgimp2.0 2.4.2-0ubuntu0.7.10.1 [564kB]
Des:37 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main libpoppler2 0.6-0ubuntu2.1 [662kB]
Des:38 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main libpoppler-glib2 0.6-0ubuntu2.1 [99,8kB]
Des:39 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main librsvg2-common 2.18.2-1 [62,6kB]
Des:40 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libgsf-1-common 1.14.7-0ubuntu1 [50,0kB]
Des:41 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libgsf-1-114 1.14.7-0ubuntu1 [141kB]
Des:42 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main librsvg2-2 2.18.2-1 [137kB]
34,2MB descarregats en 1m48s (316kB/s)
S'estan extraient les plantilles dels paquets: 100%
S'està seleccionant el paquet liblzo2-2 prèviament no seleccionat.
(S'està llegint la base de dades ... hi ha 127852 fitxers i directoris instal·lats actualment.)
S'està desempaquetant liblzo2-2 (de .../liblzo2-2_2.02-3_i386.deb) ...
S'està preparant per a reemplaçar zlib1g 1:1.2.3-13ubuntu4 (fent servir .../zlib1g_1%3a1.2.3.3.dfsg-5ubuntu2_i386.deb) ...
S'està desempaquetant el reemplaçament de zlib1g ...
S'està configurant zlib1g (1.2.3.3.dfsg-5ubuntu2) ...

(S'està llegint la base de dades ... hi ha 127859 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar libopencdk8 0.5.9-2build1 (fent servir .../libopencdk8_0.5.13-2_i386.deb) ...
S'està desempaquetant el reemplaçament de libopencdk8 ...
S'està preparant per a reemplaçar libgnutls13 1.4.4-3build1 (fent servir .../libgnutls13_1.6.3-1build1_i386.deb) ...
S'està desempaquetant el reemplaçament de libgnutls13 ...
S'està seleccionant el paquet libkeyutils1 prèviament no seleccionat.
S'està desempaquetant libkeyutils1 (de .../libkeyutils1_1.2-3_i386.deb) ...
S'està preparant per a reemplaçar libkrb53 1.4.4-5ubuntu3.3 (fent servir .../libkrb53_1.6.dfsg.1-7build1_i386.deb) ...
S'està desempaquetant el reemplaçament de libkrb53 ...
S'està preparant per a reemplaçar libcupsys2 1.2.8-0ubuntu8.2 (fent servir .../libcupsys2_1.3.2-1ubuntu7.5_i386.deb) ...
S'està desempaquetant el reemplaçament de libcupsys2 ...
S'està preparant per a reemplaçar libfreetype6 2.2.1-5ubuntu1.1 (fent servir .../libfreetype6_2.3.5-1ubuntu4_i386.deb) ...
S'està desempaquetant el reemplaçament de libfreetype6 ...
S'està seleccionant el paquet libjasper1 prèviament no seleccionat.
S'està desempaquetant libjasper1 (de .../libjasper1_1.900.1-3_i386.deb) ...
S'està preparant per a reemplaçar libstdc++6 4.1.2-0ubuntu4 (fent servir .../libstdc++6_4.2.1-5ubuntu4_i386.deb) ...
S'està desempaquetant el reemplaçament de libstdc++6 ...
S'està configurant libstdc++6 (4.2.1-5ubuntu4) ...

(S'està llegint la base de dades ... hi ha 127874 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar libxml2 2.6.27.dfsg-1ubuntu3.1 (fent servir .../libxml2_2.6.30.dfsg-2ubuntu1.1_i386.deb) ...
S'està desempaquetant el reemplaçament de libxml2 ...
S'està preparant per a reemplaçar kdelibs4c2a 4:3.5.6-0ubuntu14.2 (fent servir .../kdelibs4c2a_4%3a3.5.8-0ubuntu3.3_i386.deb) ...
S'està desempaquetant el reemplaçament de kdelibs4c2a ...
S'està preparant per a reemplaçar kdelibs-data 4:3.5.6-0ubuntu14.2 (fent servir .../kdelibs-data_4%3a3.5.8-0ubuntu3.3_all.deb) ...
S'està desempaquetant el reemplaçament de kdelibs-data ...
S'està seleccionant el paquet libexiv2-0 prèviament no seleccionat.
S'està desempaquetant libexiv2-0 (de .../libexiv2-0_0.15-1ubuntu2_i386.deb) ...
S'està preparant per a reemplaçar libdbus-1-3 1.0.2-1ubuntu4 (fent servir .../libdbus-1-3_1.1.1-3ubuntu4_i386.deb) ...
S'està desempaquetant el reemplaçament de libdbus-1-3 ...
S'està preparant per a reemplaçar libhal1 0.5.8.1-4ubuntu12 (fent servir .../libhal1_0.5.9.1-6ubuntu5_i386.deb) ...
S'està desempaquetant el reemplaçament de libhal1 ...
S'està preparant per a reemplaçar libgphoto2-port0 2.3.0-0ubuntu4 (fent servir .../libgphoto2-port0_2.4.0-2ubuntu2_i386.deb) ...
S'està desempaquetant el reemplaçament de libgphoto2-port0 ...
S'està preparant per a reemplaçar libgphoto2-2 2.3.0-0ubuntu4 (fent servir .../libgphoto2-2_2.4.0-2ubuntu2_i386.deb) ...
S'està desempaquetant el reemplaçament de libgphoto2-2 ...
S'està seleccionant el paquet libkdcraw1 prèviament no seleccionat.
S'està desempaquetant libkdcraw1 (de .../libkdcraw1_0.1.1-2_i386.deb) ...
S'està seleccionant el paquet libkexiv2-1 prèviament no seleccionat.
S'està desempaquetant libkexiv2-1 (de .../libkexiv2-1_0.1.5-1ubuntu2_i386.deb) ...
S'està preparant per a reemplaçar libsqlite3-0 3.3.13-0ubuntu1 (fent servir .../libsqlite3-0_3.4.2-1build1_i386.deb) ...
S'està desempaquetant el reemplaçament de libsqlite3-0 ...
S'està preparant per a reemplaçar libwmf0.2-7 0.2.8.4-2build1 (fent servir .../libwmf0.2-7_0.2.8.4-6_i386.deb) ...
Cleaning up font configuration of libwmf0.2-7...
Cleaning up category type1..
Cleaning up category truetype..
S'està desempaquetant el reemplaçament de libwmf0.2-7 ...
(S'està llegint la base de dades ... hi ha 127997 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant gtk-qt-engine ...
(S'està llegint la base de dades ... hi ha 127983 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar libgtk2.0-common 2.10.11-0ubuntu3 (fent servir .../libgtk2.0-common_2.12.0-1ubuntu3_all.deb) ...
S'està desempaquetant el reemplaçament de libgtk2.0-common ...
S'està preparant per a reemplaçar libatk1.0-0 1.18.0-0ubuntu1 (fent servir .../libatk1.0-0_1.20.0-0ubuntu1_i386.deb) ...
S'està desempaquetant el reemplaçament de libatk1.0-0 ...
S'està preparant per a reemplaçar libpango1.0-common 1.16.2-0ubuntu1 (fent servir .../libpango1.0-common_1.18.3-0ubuntu1_all.deb) ...
Cleaning up font configuration of pango...
Cleaning up category xfont..
S'està desempaquetant el reemplaçament de libpango1.0-common ...
S'està preparant per a reemplaçar libpango1.0-0 1.16.2-0ubuntu1 (fent servir .../libpango1.0-0_1.18.3-0ubuntu1_i386.deb) ...
S'està desempaquetant el reemplaçament de libpango1.0-0 ...
S'està preparant per a reemplaçar libxdamage1 1:1.0.3-3 (fent servir .../libxdamage1_1%3a1.1.1-3_i386.deb) ...
S'està desempaquetant el reemplaçament de libxdamage1 ...
S'està preparant per a reemplaçar libgtk2.0-0 2.10.11-0ubuntu3 (fent servir .../libgtk2.0-0_2.12.0-1ubuntu3_i386.deb) ...
S'està desempaquetant el reemplaçament de libgtk2.0-0 ...
S'està seleccionant el paquet libgpod2 prèviament no seleccionat.
S'està desempaquetant libgpod2 (de .../libgpod2_0.5.2-2_i386.deb) ...
S'està preparant per a reemplaçar libktnef1 4:3.5.6-0ubuntu6 (fent servir .../libktnef1_4%3a3.5.7enterprise20070926-0ubuntu2.1_i386.deb) ...
S'està desempaquetant el reemplaçament de libktnef1 ...
S'està preparant per a reemplaçar libkdepim1a 4:3.5.6-0ubuntu6 (fent servir .../libkdepim1a_4%3a3.5.7enterprise20070926-0ubuntu2.1_i386.deb) ...
S'està desempaquetant el reemplaçament de libkdepim1a ...
S'està reemplaçant fitxers del paquet antic korganizer ...
S'està preparant per a reemplaçar libkcal2b 4:3.5.6-0ubuntu6 (fent servir .../libkcal2b_4%3a3.5.7enterprise20070926-0ubuntu2.1_i386.deb) ...
S'està desempaquetant el reemplaçament de libkcal2b ...
(S'està llegint la base de dades ... hi ha 128018 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant gimp ...
(S'està llegint la base de dades ... hi ha 127807 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar gimp-data 2.2.13-1ubuntu4.4 (fent servir .../gimp-data_2.4.2-0ubuntu0.7.10.1_all.deb) ...
S'està desempaquetant el reemplaçament de gimp-data ...
S'està seleccionant el paquet gimp prèviament no seleccionat.
S'està desempaquetant gimp (de .../gimp_2.4.2-0ubuntu0.7.10.1_i386.deb) ...
S'està preparant per a reemplaçar libdbus-glib-1-2 0.73-1 (fent servir .../libdbus-glib-1-2_0.74-1_i386.deb) ...
S'està desempaquetant el reemplaçament de libdbus-glib-1-2 ...
S'està preparant per a reemplaçar libgimp2.0 2.2.13-1ubuntu4.4 (fent servir .../libgimp2.0_2.4.2-0ubuntu0.7.10.1_i386.deb) ...
S'està desempaquetant el reemplaçament de libgimp2.0 ...
S'està seleccionant el paquet libpoppler2 prèviament no seleccionat.
S'està desempaquetant libpoppler2 (de .../libpoppler2_0.6-0ubuntu2.1_i386.deb) ...
S'està seleccionant el paquet libpoppler-glib2 prèviament no seleccionat.
S'està desempaquetant libpoppler-glib2 (de .../libpoppler-glib2_0.6-0ubuntu2.1_i386.deb) ...
S'està preparant per a reemplaçar librsvg2-common 2.16.0-0ubuntu2 (fent servir .../librsvg2-common_2.18.2-1_i386.deb) ...
S'està desempaquetant el reemplaçament de librsvg2-common ...
S'està preparant per a reemplaçar libgsf-1-common 1.14.3-1ubuntu2 (fent servir .../libgsf-1-common_1.14.7-0ubuntu1_all.deb) ...
S'està desempaquetant el reemplaçament de libgsf-1-common ...
S'està preparant per a reemplaçar libgsf-1-114 1.14.3-1ubuntu2 (fent servir .../libgsf-1-114_1.14.7-0ubuntu1_i386.deb) ...
S'està desempaquetant el reemplaçament de libgsf-1-114 ...
S'està preparant per a reemplaçar librsvg2-2 2.16.0-0ubuntu2 (fent servir .../librsvg2-2_2.18.2-1_i386.deb) ...
S'està desempaquetant el reemplaçament de librsvg2-2 ...
S'està configurant liblzo2-2 (2.02-3) ...

S'està configurant libopencdk8 (0.5.13-2) ...

S'està configurant libgnutls13 (1.6.3-1build1) ...

S'està configurant libkeyutils1 (1.2-3) ...

S'està configurant libkrb53 (1.6.dfsg.1-7build1) ...

S'està configurant libcupsys2 (1.3.2-1ubuntu7.5) ...

S'està configurant libfreetype6 (2.3.5-1ubuntu4) ...

S'està configurant libjasper1 (1.900.1-3) ...

S'està configurant libxml2 (2.6.30.dfsg-2ubuntu1.1) ...

S'està configurant kdelibs-data (3.5.8-0ubuntu3.3) ...
S'està instal·lant una versió nova del fitxer de configuració /etc/kde3/ksslcalist ...
S'està instal·lant una versió nova del fitxer de configuració /etc/kde3/ui/ui_standards.rc ...
S'està instal·lant una versió nova del fitxer de configuració /etc/xdg/menus/kde-applications.menu ...

S'està configurant kdelibs4c2a (3.5.8-0ubuntu3.3) ...

S'està configurant libexiv2-0 (0.15-1ubuntu2) ...

S'està configurant libdbus-1-3 (1.1.1-3ubuntu4) ...

S'està configurant libhal1 (0.5.9.1-6ubuntu5) ...

S'està configurant libgphoto2-port0 (2.4.0-2ubuntu2) ...

S'està configurant libgphoto2-2 (2.4.0-2ubuntu2) ...

S'està configurant libkdcraw1 (0.1.1-2) ...

S'està configurant libkexiv2-1 (0.1.5-1ubuntu2) ...

S'està configurant libsqlite3-0 (3.4.2-1build1) ...

S'està configurant digikam (0.9.2-2ubuntu2) ...

S'està configurant gwenview (1.4.1-1ubuntu2) ...

S'està configurant libgtk2.0-common (2.12.0-1ubuntu3) ...
S'està configurant libatk1.0-0 (1.20.0-0ubuntu1) ...

S'està configurant libpango1.0-common (1.18.3-0ubuntu1) ...
Cleaning up font configuration of pango...
Cleaning up category xfont..
Updating font configuration of pango...
Cleaning up category xfont..
Updating category xfont..

S'està configurant libpango1.0-0 (1.18.3-0ubuntu1) ...

S'està configurant libxdamage1 (1.1.1-3) ...

S'està configurant libgtk2.0-0 (2.12.0-1ubuntu3) ...
Removing generated module files coming from the previous Gtk binary version...
s'ha eliminat «/etc/gtk-2.0/gdk-pixbuf.loaders»
s'ha eliminat «/etc/gtk-2.0/gtk.immodules»

S'està configurant libwmf0.2-7 (0.2.8.4-6) ...
Updating font configuration of libwmf0.2-7...
Cleaning up category type1..
Cleaning up category truetype..
Updating category truetype..
Updating category type1..

S'està configurant libgpod2 (0.5.2-2) ...

S'està configurant libktnef1 (3.5.7enterprise20070926-0ubuntu2.1) ...

S'està configurant gimp-data (2.4.2-0ubuntu0.7.10.1) ...
S'està instal·lant una versió nova del fitxer de configuració /etc/gimp/2.0/gimprc ...
S'està instal·lant una versió nova del fitxer de configuració /etc/gimp/2.0/gtkrc ...
S'està instal·lant una versió nova del fitxer de configuració /etc/gimp/2.0/ps-menurc ...
S'està instal·lant una versió nova del fitxer de configuració /etc/gimp/2.0/sessionrc ...
S'està instal·lant una versió nova del fitxer de configuració /etc/gimp/2.0/templaterc ...
S'està instal·lant una versió nova del fitxer de configuració /etc/gimp/2.0/unitrc ...

S'està configurant libdbus-glib-1-2 (0.74-1) ...

S'està configurant libgimp2.0 (2.4.2-0ubuntu0.7.10.1) ...

S'està configurant libpoppler2 (0.6-0ubuntu2.1) ...

S'està configurant libpoppler-glib2 (0.6-0ubuntu2.1) ...

S'està configurant libgsf-1-common (1.14.7-0ubuntu1) ...
S'està configurant libgsf-1-114 (1.14.7-0ubuntu1) ...

S'està configurant librsvg2-2 (2.18.2-1) ...

S'està configurant gimp (2.4.2-0ubuntu0.7.10.1) ...

S'està configurant librsvg2-common (2.18.2-1) ...
S'està configurant libkcal2b (3.5.7enterprise20070926-0ubuntu2.1) ...

S'està configurant libkdepim1a (3.5.7enterprise20070926-0ubuntu2.1) ...

S'està configurant kipi-plugins (0.1.4-1build1) ...

irene@PELEGRI:~$ sudo aptitude update
Obté:1 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy Release.gpg [191B]
Obté:2 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main Translation-ca [6978B]
Obté:3 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-ca
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-ca
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-ca
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-ca
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/restricted Translation-ca
Obté:4 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/universe Translation-ca [1981B]
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/multiverse Translation-ca
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Obté:5 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main Translation-ca
Ign [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/restricted Translation-ca
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy Release
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates Release
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/restricted Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/restricted Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/universe Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/universe Sources
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/multiverse Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/multiverse Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/restricted Packages
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main Sources
Prem [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/restricted Sources
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Prem [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources
S'han recollit 8962B en 0s (11,3kB/s)
S'està llegint la llista de paquets... Fet
irene@PELEGRI:~$ sudo aptitude safe-upgrade
Ordre desconeguda "safe-upgrade"
aptitude 0.4.4
Utilització: aptitude [-S nomfitxer] [-u|-i]
       aptitude [opcions] <acció> ...
  Accions (si no s'han especificat, l'aptitude s'executarà en mode interactiu):

 install       - Instal·la/actualitza els paquets
 remove        - Suprimeix els paquets
 purge          - Suprimeix els paquets i els corresponents fitxers de configuració
 hold          - Deixa els paquets congelats
 unhold        - Cancel·la l'ordre de congelació d'un paquet
 markauto      - Marca els paquets com a instal·lats automàticament
 unmarkauto    - Marca els paquets com a instal·lats manualment
 forbid-version - Prohibeix l'actualització a una versió específica d'un paquet.
 update        - Baixa les llistes dels paquets nous/actualitzables
 upgrades      - Realitza una actualització segura
 dist-upgrade  - Realitza una actualització, probablement instal·lant i suprimint paquets
 forget-net     - Oblida quins paquets són "nous"
 search        - Cerca un paquet pel seu nom i/o expressió
 mostra        - Mostra informació detallada d'un paquet
 clean         - Suprimeix els fitxers dels paquets baixats
 autoclean     - Suprimeix els fitxers dels paquets baixats antics
 changelog    - Visualitza un registre de modificacions d'un paquet
 download      - Baixa el fitxer .deb d'un paquet
 torna a instal·lar     - Descarrega i (possiblament) torna a instal·lar un paquet ja instal·lat

  Opcions:
 -h             Aquest text d'ajuda
 -s             Simula les accions però no les duguis a terme.
 -d          Baixa els paquets però n'instal·lis o suprimeixis cap.
 -P             Pregunta permanentment les confirmacions o accions
 -y             Assumeix que la resposta a les preguntes sí/noo és 'sí'
 -F format      Especifica un format per a la visualització dels resultats de la cerca; fes una ullada al manual
 -O ordre       Especifica el mode en que s'han d'ordenar els resultats de la cerca, fes una ullada al manual
 -w amplada      Especifica l'amplada de la visualització pel formatat dels resultats de la cerca
 -f       Intent agressiu de resoldre els errors dels paquets.
 -V           Mostra les versions dels programes a instal·lar.
 -D           Mostra les dependències dels paquets modificats automàticament.
 -Z     Mostra els canvis de la mida instal·lada per a cada paquet.
 -v       Mostra la informació extra. (s'utilitza múltiples vegades)
 -t [versió]   Especifica la versió de llançament de la qual s'haurien d'instal·lar les paquets
 -q            En mode línies d'ordres, suprimeix els indicadors de progrés incremental.
 -o clau=val   Defineix directament l'opció de configuració 'clau'
 --with(out)-recommends  Especifica si s'han de tractar o no les recomanacions com
                dependències fortes
 -S nomf: Llegeix la informació d'estat estesa de l'aptitude del nom.
 -u       : Baixa una nova llista de paquets a l'inici.
 -i          : Executa la instal·lació a l'inici.

                  L'aptitude no té super poders bovins.
irene@PELEGRI:~$

---

### Post by papapep on 2008-02-20
> És llarguíssim, i al final em diu que la meva aptitud no té superpoders bovins (però si sóc taure!!!)

Hhehehe, tot i els meus minsos coneixements de biologia, crec que, com a mínim, sou de la mateixa família :-D

Molt bé. Em fa l'efecte que hem fet el cim. 
Respecte l'error de la manca de poders bovins de l'aptitude, ve donat per que la versió que tens tu, 7.04, encara feia servir el format antic de la ordre:

```
sudo aptitude upgrade
```

A veure què tal va ;-)

---

### Post by lluisanunez on 2008-02-20
```
                   L'aptitude no té super poders bovins.

```Ei, quina barra que té, dir això sense que li diguis ni "moo"!

---

### Post by ipelegri6 on 2008-02-20
je, je... Sí que sembla un remugant, perquè s'ha quedat una bona estona paint lletres...

M'he quedat sense Firefox, ara. Quan intento escriure la finestra desapareix. Intento escriure des del konkeror, però s'entesta a obrir el firefox, no sé si me'n sortiré...

No sabria dir si ha funcionat. Al final, després de més de mitja hora, ha dit:

Generation complete.

E: Failed to fetch [http://ad.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kmix_3.5.8-0ubuntu1_i386.deb:](http://ad.archive.ubuntu.com/ubuntu/pool/main/k/kdemultimedia/kmix_3.5.8-0ubuntu1_i386.deb:) Connexió finalitzada [IP: 91.189.88.31 80]
irene@PELEGRI:~$

Què faig, reinicio? Tanco el terminal? Espero?

---

### Post by papapep on 2008-02-20
mmm...ostres, no sé, després de quina ordre t'ha mostrat el missatge que dius?

I abans d'això:

> Generation complete.

No ha dit res?

---

### Post by ipelegri6 on 2008-02-20
S'està configurant hwdb-client-gnome (0.6.11.1) ...
S'està configurant hal-device-manager (0.5.9.1-6ubuntu5) ...

S'està configurant inkscape (0.45.1-1ubuntu5) ...

S'està configurant usplash (0.5.7) ...
S'està instal·lant una versió nova del fitxer de configuració /etc/init.d/usplash ...
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic

S'està configurant kubuntu-artwork-usplash (7.10-28) ...
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic

S'està configurant libgnome-desktop-2 (2.20.1-0ubuntu1) ...

S'està configurant libgnome-menu2 (2.20.1-0ubuntu1) ...

S'està configurant libpanel-applet2-0 (2.20.1-0ubuntu1) ...

S'està configurant xorg (7.2-5ubuntu13) ...
S'està configurant language-pack-ca-base (7.10+20071012) ...
Generating locales...
  ca_AD.UTF-8... done
  ca_ES.UTF-8... done
  ca_ES.UTF-8@valencia... done
  ca_FR.UTF-8... done
  ca_IT.UTF-8... done
Generation complete.

S'està configurant language-pack-en-base (7.10+20071012) ...
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.

Estic fent virgueries entre el konkeror i el firefox que se'm tanca.

---

### Post by papapep on 2008-02-20
Bé. En tot cas, carrega-te'l i torna'l a instal·lar, a veure si solucionem els problemes:

```
sudo aptitude purge firefox
```

```
sudo aptitude install firefox
```

---

### Post by ipelegri6 on 2008-02-20
Ja ho he fet i ara sembla que no es tanca...
Què faig?

---

### Post by ipelegri6 on 2008-02-20
Sí, ara funciona, tot i que té un aspecte un xic diferent :-)
Haig de fer alguna comprovació més abans de tancar?
Irene

---

### Post by papapep on 2008-02-20
> Què faig?

Per aconseguir què? No dius que ara ja va bé? Encara tens altres problemes?? :-)

---

### Post by ipelegri6 on 2008-02-20
Per instal·lar l'eXelearning, que era el meu objectiu inicial

---

### Post by ipelegri6 on 2008-02-20
A més, l'openoffice continua sense funcionar...

---

### Post by papapep on 2008-02-20
Amb tants posts, i dies, que portem entre el principi i el punt actual d'aquest fil ja no m'enrecordava de l'eXelearning!! :-D

Respecte l'openoffice, què vol dir "l'openoffice continua sense funcionar"? No s'engega? O s'engega i va malament? Et surt al menú de programes, o ni això?

Fes:

```
sudo aptitude search openoffice.org |grep i\ 
```

**ATENCIÓ: Després de la "i" i la barra inclinada al revés "\" ha d'haver [COLOR="Red"]un[/COLOR] espai.**

Enganxa el que et respongui, si us plau.

---

### Post by ipelegri6 on 2008-02-20
je, je, jo casi m'havia oblidat i em pensava que era aquí pel secondlife, que tampoc em funciona.

Bé. ho he fet i m'ha dit (això ja sembla el joc dels missatges ;-) )

irene@PELEGRI:~$ sudo aptitude search openoffice.org |grep i\
[sudo] password for irene:
E: No s'ha pogut blocar /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
i   openclipart-openoffice.org      - clip art for OpenOffice.org gallery
i   openoffice.org-calc             - OpenOffice.org office suite - spreadsheet
i   openoffice.org-common           - OpenOffice.org office suite architecture i
i   openoffice.org-core             - OpenOffice.org office suite architecture d
i   openoffice.org-draw             - OpenOffice.org office suite - drawing
p   openoffice.org-help-hi-in       - Hindi help for OpenOffice.org
i   openoffice.org-hyphenation      - Hyphenation patterns for OpenOffice.org
v   openoffice.org-hyphenation-fi   -
i   openoffice.org-impress          - OpenOffice.org office suite - presentation
i   openoffice.org-kde              - KDE Integration for OpenOffice.org (Widget
p   openoffice.org-l10n-bn          - Bengali language package for OpenOffice.or
i   openoffice.org-l10n-ca          - Catalan language package for OpenOffice.or
i   openoffice.org-l10n-common      - common files for OpenOffice.org language a
i   openoffice.org-l10n-en-gb       - English_british language package for OpenO
i   openoffice.org-l10n-en-za       - English_southafrican language package for
i   openoffice.org-l10n-es          - Spanish language package for OpenOffice.or
p   openoffice.org-l10n-fa          - Farsi language package for OpenOffice.org
p   openoffice.org-l10n-fi          - Finnish language package for OpenOffice.or
p   openoffice.org-l10n-gu-in       - Gujarati language package for OpenOffice.o
p   openoffice.org-l10n-hi-in       - Hindi language package for OpenOffice.org
p   openoffice.org-l10n-mr-in       - Marathi language package for OpenOffice.or
p   openoffice.org-l10n-pa-in       - Punjabi language package for OpenOffice.or
p   openoffice.org-l10n-ss          - Swazi language package for OpenOffice.org
p   openoffice.org-l10n-sw          - Swahili language package for OpenOffice.or
p   openoffice.org-l10n-th          - Thai language package for OpenOffice.org
p   openoffice.org-l10n-vi          - Vietnamese language package for OpenOffice
i   openoffice.org-math             - OpenOffice.org office suite - equation edi
v   openoffice.org-spellcheck-fi    -
i   openoffice.org-style-crystal    - Crystal symbol style for OpenOffice.org
i   openoffice.org-style-human      - Human symbol style for OpenOffice.org
i   openoffice.org-thesaurus-en-us  - English Thesaurus for OpenOffice.org
i   openoffice.org-writer           - OpenOffice.org office suite - word process
v   openoffice.org2-l10n-fi         -
v   openoffice.org2-l10n-vi         -

No funcionar vol dir que el clico al menú però no fa res. Abans sortia la finestreta amb el nom i el rellotge de banda però no es carregava de blau i la finestra marxava. Ara ja ni això.

He provat de desinstal·lar amb l'adept i tornar a instal·lar però continua igual.

---

### Post by papapep on 2008-02-20
Tens l'adept o synaptic o qualsevol altre programa obert?? No pots tenir-ne cap d'aquests oberts mentre fas anar l'aptitude o apt-get o el dpkg, això crea conflictes.

---

### Post by ipelegri6 on 2008-02-20
El que fa la ignorància...
Estava mirant l'altra, el que em diu que tinc 77 paquets actualitzables, però suposo que deu fer el mateix efecte, no?
Ara ho he tornat a fer i m'ha dit:


i   openclipart-openoffice.org      - clip art for OpenOffice.org gallery
i   openoffice.org-calc             - OpenOffice.org office suite - spreadsheet
i   openoffice.org-common           - OpenOffice.org office suite architecture i
i   openoffice.org-core             - OpenOffice.org office suite architecture d
i   openoffice.org-draw             - OpenOffice.org office suite - drawing
p   openoffice.org-help-hi-in       - Hindi help for OpenOffice.org
i   openoffice.org-hyphenation      - Hyphenation patterns for OpenOffice.org
v   openoffice.org-hyphenation-fi   -
i   openoffice.org-impress          - OpenOffice.org office suite - presentation
i   openoffice.org-kde              - KDE Integration for OpenOffice.org (Widget
p   openoffice.org-l10n-bn          - Bengali language package for OpenOffice.or
i   openoffice.org-l10n-ca          - Catalan language package for OpenOffice.or
i   openoffice.org-l10n-common      - common files for OpenOffice.org language a
i   openoffice.org-l10n-en-gb       - English_british language package for OpenO
i   openoffice.org-l10n-en-za       - English_southafrican language package for
i   openoffice.org-l10n-es          - Spanish language package for OpenOffice.or
p   openoffice.org-l10n-fa          - Farsi language package for OpenOffice.org
p   openoffice.org-l10n-fi          - Finnish language package for OpenOffice.or
p   openoffice.org-l10n-gu-in       - Gujarati language package for OpenOffice.o
p   openoffice.org-l10n-hi-in       - Hindi language package for OpenOffice.org
p   openoffice.org-l10n-mr-in       - Marathi language package for OpenOffice.or
p   openoffice.org-l10n-pa-in       - Punjabi language package for OpenOffice.or
p   openoffice.org-l10n-ss          - Swazi language package for OpenOffice.org
p   openoffice.org-l10n-sw          - Swahili language package for OpenOffice.or
p   openoffice.org-l10n-th          - Thai language package for OpenOffice.org
p   openoffice.org-l10n-vi          - Vietnamese language package for OpenOffice
i   openoffice.org-math             - OpenOffice.org office suite - equation edi
v   openoffice.org-spellcheck-fi    -
i   openoffice.org-style-crystal    - Crystal symbol style for OpenOffice.org
i   openoffice.org-style-human      - Human symbol style for OpenOffice.org
i   openoffice.org-thesaurus-en-us  - English Thesaurus for OpenOffice.org
i   openoffice.org-writer           - OpenOffice.org office suite - word process
v   openoffice.org2-l10n-fi         -
v   openoffice.org2-l10n-vi         -
irene@PELEGRI:~$  

És greu?

---

### Post by papapep on 2008-02-20
> És greu?

hhehehhe, tranquila, n'hem curat de "molt pitjors"...

Si vols podem fer com amb el firefox, eliminar-lo completament i tornar a començar (amb la resta de programes de gestió de paquets tancats! ;-)):

```
sudo aptitude purge openoffice.org openoffice.org2
```

```
sudo aptitude install openoffice.org2
```

---

### Post by ipelegri6 on 2008-02-20
Ok!

---

### Post by ipelegri6 on 2008-02-20
Ja ha fet coses, ja, però no ha funcionat. Continua sense obrir-se. No serà que ha perdut la connexió amb el menú?
Digo yo...

---

### Post by ipelegri6 on 2008-02-20
Espera, que et passo el text, per si de cas el necessites...

irene@PELEGRI:~$ sudo aptitude purge openoffice.org openoffice.org2
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
S'està llegint la informació d'estat estesa
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
Nota: s'està seleccionant "openoffice.org" en comptes del
      paquet virtual "openoffice.org2"
Els paquets següents s'han apartat automàticament:
  apt apt-utils dpkg-dev libcompress-zlib-perl libjack0.100.0-0
  libmjpegtools0c2a libwnck-common linux-image-generic ntfs-3g
  python-gnome2-desktop transcode
Els paquets següents s'han apartat:
  adept-batch adept-installer adept-manager adept-notifier adept-updater
  amarok amarok-xine apport-qt aptitude bind9-host bogofilter-bdb brltty
  cupsys debtags dmsetup dnsutils dpkg eject gcj-4.1-base gij gij-4.1
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-good hal hpijs hplip hplip-data iproute
  kaffeine-xine kde-guidance kdebluetooth kdegraphics-kfile-plugins kexi
  kmix knetworkmanager koffice-data koffice-libs kubuntu-default-settings
  libakode2 libblkid1 libgcj-bc libgpgme11 libk3b2 libpam-modules
  libsndfile1 libtunepimp5 libxine1 linux-headers-generic
  mozilla-thunderbird mplayer netbase network-manager python-apport
  python-apt python-central python-launchpad-bugs python2.5 python2.5-dev
  python2.5-minimal synaptic ttf-indic-fonts vorbis-tools wireless-tools
  wvdial xserver-xorg-video-all
0 paquets actualitzats, 0 instal·lats, 0 a suprimir i 77 a no actualitzar.
Es necessita obtenir 0B d'arxius. Després del desempaquetat s'utilitzaran 0B.
S'està escrivint la informació d'estat estesa... Fet
irene@PELEGRI:~$ sudo aptitude install openoffice.org2
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
S'està llegint la informació d'estat estesa
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
Nota: s'està seleccionant "openoffice.org" en comptes del
      paquet virtual "openoffice.org2"
Els paquets següents s'han apartat automàticament:
  apt apt-utils dpkg-dev libcompress-zlib-perl libjack0.100.0-0
  libmjpegtools0c2a libwnck-common linux-image-generic ntfs-3g
  python-gnome2-desktop transcode
Els paquets nous següents s'instal·laran automàticament:<
  libhsqldb-java libservlet2.4-java openoffice.org-base
  openoffice.org-filter-binfilter openoffice.org-filter-mobiledev
  openoffice.org-java-common openoffice.org-officebean
Els paquets següents s'han apartat:
  adept-batch adept-installer adept-manager adept-notifier adept-updater
  amarok amarok-xine apport-qt aptitude bind9-host bogofilter-bdb brltty
  cupsys debtags dmsetup dnsutils dpkg eject gcj-4.1-base gij gij-4.1
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-good hal hpijs hplip hplip-data iproute
  kaffeine-xine kde-guidance kdebluetooth kdegraphics-kfile-plugins kexi
  kmix knetworkmanager koffice-data koffice-libs kubuntu-default-settings
  libakode2 libblkid1 libgcj-bc libgpgme11 libk3b2 libpam-modules
  libsndfile1 libtunepimp5 libxine1 linux-headers-generic
  mozilla-thunderbird mplayer netbase network-manager python-apport
  python-apt python-central python-launchpad-bugs python2.5 python2.5-dev
  python2.5-minimal synaptic ttf-indic-fonts vorbis-tools wireless-tools
  wvdial xserver-xorg-video-all
Els paquets nous següents s'instal·laran:
  libhsqldb-java libservlet2.4-java openoffice.org openoffice.org-base
  openoffice.org-filter-binfilter openoffice.org-filter-mobiledev
  openoffice.org-java-common openoffice.org-officebean
0 paquets actualitzats, 8 instal·lats, 0 a suprimir i 77 a no actualitzar.
Es necessita obtenir 14,4MB d'arxius. Després del desempaquetat s'utilitzaran 37,8MB.
Esteu segur de voler continuar? [Y/n/?] y
S'està escrivint la informació d'estat estesa... Fet
Obté:1 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libservlet2.4-java 5.0.30-6ubuntu1 [143kB]
Obté:2 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main libhsqldb-java 1.8.0.8-1ubuntu1 [949kB]
Obté:3 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main openoffice.org-java-common 1:2.3.0-1ubuntu5.3 [2781kB]
Obté:4 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main openoffice.org-base 1:2.3.0-1ubuntu5.3 [2501kB]
Obté:5 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main openoffice.org 1:2.3.0-1ubuntu5.3 [4972B]
Obté:6 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main openoffice.org-filter-binfilter 1:2.3.0-1ubuntu5.3 [7849kB]
Obté:7 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/universe openoffice.org-filter-mobiledev 1:2.3.0-1ubuntu5 [95,1kB]
Obté:8 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy-updates/main openoffice.org-officebean 1:2.3.0-1ubuntu5.3 [49,5kB]
S'han recollit 14,4MB en 45s (315kB/s)
S'està seleccionant el paquet libservlet2.4-java prèviament no seleccionat.
(S'està llegint la base de dades ... hi ha 140168 fitxers i directoris instal·lats actualment.)
S'està desempaquetant libservlet2.4-java (de .../libservlet2.4-java_5.0.30-6ubuntu1_all.deb) ...
S'està seleccionant el paquet libhsqldb-java prèviament no seleccionat.
S'està desempaquetant libhsqldb-java (de .../libhsqldb-java_1.8.0.8-1ubuntu1_all.deb) ...
S'està seleccionant el paquet openoffice.org-java-common prèviament no seleccionat.
S'està desempaquetant openoffice.org-java-common (de .../openoffice.org-java-common_1%3a2.3.0-1ubuntu5.3_all.deb) ...
S'està seleccionant el paquet openoffice.org-base prèviament no seleccionat.
S'està desempaquetant openoffice.org-base (de .../openoffice.org-base_1%3a2.3.0-1ubuntu5.3_i386.deb) ...
S'està seleccionant el paquet openoffice.org prèviament no seleccionat.
S'està desempaquetant openoffice.org (de .../openoffice.org_1%3a2.3.0-1ubuntu5.3_i386.deb) ...
S'està seleccionant el paquet openoffice.org-filter-binfilter prèviament no seleccionat.
S'està desempaquetant openoffice.org-filter-binfilter (de .../openoffice.org-filter-binfilter_1%3a2.3.0-1ubuntu5.3_i386.deb) ...
S'està seleccionant el paquet openoffice.org-filter-mobiledev prèviament no seleccionat.
S'està desempaquetant openoffice.org-filter-mobiledev (de .../openoffice.org-filter-mobiledev_1%3a2.3.0-1ubuntu5_all.deb) ...
S'està seleccionant el paquet openoffice.org-officebean prèviament no seleccionat.
S'està desempaquetant openoffice.org-officebean (de .../openoffice.org-officebean_1%3a2.3.0-1ubuntu5.3_i386.deb) ...
S'està configurant libservlet2.4-java (5.0.30-6ubuntu1) ...
S'està configurant libhsqldb-java (1.8.0.8-1ubuntu1) ...

S'està configurant openoffice.org-java-common (2.3.0-1ubuntu5.3) ...

S'està configurant openoffice.org-base (2.3.0-1ubuntu5.3) ...

S'està configurant openoffice.org (2.3.0-1ubuntu5.3) ...

S'està configurant openoffice.org-filter-binfilter (2.3.0-1ubuntu5.3) ...

S'està configurant openoffice.org-filter-mobiledev (2.3.0-1ubuntu5) ...

S'està configurant openoffice.org-officebean (2.3.0-1ubuntu5.3) ...

irene@PELEGRI:~$

---

### Post by ipelegri6 on 2008-02-20
Una pregunta addicional: amb els paquets actualitzables que em diu que tinc l'adept_updater, què faig, li dic que endavant abans de tancar l'ordinador?

---

### Post by ipelegri6 on 2008-02-20
Uf, em sembla que ho deixo per demà...
Estic explorant i hi ha moltes coses que em donen error, per exemple el kontact:

No es pot executar l'ordre especificada. El fitxer o carpeta file:///usr/share/applications/kde/Kontact.desktop no existeix.

I d'altres que s'obren amb errors, com el kate:

No s'ha pogut trobar el tipus mime
application/octet-stream

URL erroni
file:///home/irene

O el kpdf:

No s'ha pogut trobar el tipus mime
application/octet-stream

No hi ha tipus mime instal·lats.

Moltes gràcies, hi tornaré, no ho dubtis :-) :-)

---

### Post by papapep on 2008-02-21
Per verificar si l'openoffice funciona correctament o no, fes a un terminal:

```
ooffice -writer
```

I se t'hauria d'obrir l'editor de textos.

---

### Post by ipelegri6 on 2008-02-22
Hola papapep,
En apagar i tornar a encendre l'ordinador ara sí que funcionava l'OO. En fer el que m'has dit em dóna errors però s'obre:

irene@PELEGRI:~$ ooffice -writer
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
irene@PELEGRI:~$


I funciona. L'únic que em passa ara és que moltes aplicacions (firefox, oo,...) em surten amb la interfície amb una lletra minúscula (de mida). Però vaja, funcionen.

Ara vaig per l'exelearning.
Primer punt: quin fitxer m'haig de baixar de tots els disponibles per a ubuntu a [https://eduforge.org/frs/?group_id=20?:](https://eduforge.org/frs/?group_id=20?:)

 Ubuntu Linux - Release Notes - Highlight This Release	   2008-01-21 00:00
Ubuntu Linux	
    python2.4-exe_1.02.0.3303-ubuntu1_i386.deb	9.45 MB	200	Linux i386	.deb
    python2.4-exe_1.03.0.3373-ubuntu1_i386.deb	9.51 MB	47	Linux i386	.deb
    python2.5-exe_1.02.0.3303-ubuntu1_i386.deb	9.45 MB	629	Linux i386	.deb
    python2.5-exe_1.03.0.3373-ubuntu1_i386.deb	9.51 MB	198	Linux i386	.deb
    python-exe_1.02.0.3303-ubuntu1_i386.deb	914 bytes	151	Linux i386	.deb
    python-exe_1.03.0.3373-ubuntu1_i386.deb

Jo ho havia provat amb     python2.5-exe_1.03.0.3373-ubuntu1_i386.deb, perquè no sé com decidir quin és el que necessito...

Irene

---

### Post by papapep on 2008-02-22
Jo el que vaig baixar, i com ja et vaig dir va funcionar correctament, és el [python2.5-exe_1.03.0.3373-ubuntu1_i386.deb]("https://eduforge.org/frs/download.php/758/python2.5-exe_1.03.0.3373-ubuntu1_i386.deb"), com tu.

---

### Post by SiscoGarcia on 2008-02-22
Pel que fa a la mida del text prova amb Sistema>Preferències>Aparença>Tipus de lletra (aquí pots triar el tipus de lletra i també la mida). Espero que amb això se't resolgui.

---

### Post by ipelegri6 on 2008-02-24
Ja he esbrinat perquè les lletres sortien petites: s'havia desinstal·lat la targeta gràfica i en tornar a engegar tenia només una consola. Per telèfon un amic m'ha ajudat a recuperar-la però ara encara haig d'instal·lar la NVIDIA. Bé, ja ho faré.

De moment encara no puc amb l'eXelearning. Quan ho faig obtinc l'error següent:

irene@PELEGRI:~$ cd ..
irene@PELEGRI:/home$ cd ..
irene@PELEGRI:/$ cd usr
irene@PELEGRI:/usr$ cd bin
irene@PELEGRI:/usr/bin$ cd eXe
irene@PELEGRI:/usr/bin/eXe$ sudo dpkg -i python2.5-exe_1.03.0.3373-ubuntu1_i386.deb
[sudo] password for irene:
(S'està llegint la base de dades ... hi ha 158649 fitxers i directoris instal·lats actualment.)
S'està desempaquetant python2.5-exe (de python2.5-exe_1.03.0.3373-ubuntu1_i386.deb) ...
dpkg: s'ha produït un error en processar python2.5-exe_1.03.0.3373-ubuntu1_i386.deb (--install):
 s'està intentant sobreescriure «/usr/bin/run-exe.sh», que també està en el paquet python2.4-exe
dpkg-deb: el subprocés paste ha estat finalitzat pel senyal (Broken pipe)
S'han trobat errors en processar:
 python2.5-exe_1.03.0.3373-ubuntu1_i386.deb
irene@PELEGRI:/usr/bin/eXe$

I no l'instal·la. He provat reanomenant el fitxer /usr/bin/run-exe.sh a /usr/bin/run-exe_vell.sh perquè es trobi el camí lliure i el creï de nou si vol, però no m'ha fet cas (com era previsible, perquè tampoc sé jo perquè he decidit de fer aquesta prova :confused:)

En fi, que avui m'han tornat a dir que és un programa fantàstic però jo res de res...

---

### Post by papapep on 2008-02-24
Pel tema de l'Nvidia crec que un programet que es diu [Envy]("http://albertomilone.com/nvidia_scripts1.html") et pot ajudar. Però hauries d'obrir un fil específic, si us plau.

Pel tema de l'exelearning, mostra'm que et surt en fer:

```
ls -la /usr/bin/run-exe.sh
```

---

### Post by ipelegri6 on 2008-02-25
Sí, sí, ja obriré un fil específic, i tant! I per al java, i per a secondlife ;-)
Però pas per pas.

De moment, fent el que m'has dit, la resposta és:

irene@PELEGRI:~$ ls -la /usr/bin/run-exe.sh
-rwxr-xr-x 1 root root 128 2008-02-13 17:24 /usr/bin/run-exe.sh
irene@PELEGRI:~$

---

### Post by papapep on 2008-02-25
Doncs no sóc capaç de veure per on estirar el tema...catxis...

Podríem provar a esborrar el python2.4, instal·lar l'exelearning i tornar-lo a instal·lar després. No sé si és una bestiesa....

Si vols provar-ho fes a un terminal:

```
sudo aptitude purge python2.4
```

Crec que seria interessant que abans d'acceptar el que et proposarà l'aptitude, enganxessis el missatge del que et proposa aquí, per verificar que no fem cap destrossa... :roll:

---

### Post by ipelegri6 on 2008-02-28
Hola papapep,

ho he fet i abans d'acceptar et transcric el missatge:


[sudo] password for irene:
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
S'està llegint la informació d'estat estesa
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet
Els paquets següents contenen errors.
  j2re1.4-mozilla-plugin
Els paquets següents no s'utilitzen i se suprimiran:
  libavcodec0d libdc1394-13 libdvdcss2 libfame-0.9 libjack0.100.0-0
  libntfs-3g0 libpostproc0d libpostproc1d libpvm3 libswfdec0.3
  libtotem-plparser1 linux-headers-2.6.20-16
  linux-headers-2.6.20-16-generic mozilla-firefox-locale-es-ar
  mozilla-firefox-locale-es-es openoffice.org-l10n-es transcode wspanish
Els paquets següents s'han apartat automàticament:
  language-pack-kde-ca-base language-pack-kde-es-base
Els paquets següents s'han apartat:
  language-pack-kde-en language-pack-kde-en-base language-pack-kde-es
The following partially installed packages will be configured:
  language-pack-ca language-pack-ca-base language-pack-en
  language-pack-en-base language-pack-es language-pack-es-base
  language-pack-gnome-ca language-pack-gnome-ca-base language-pack-gnome-es
  language-pack-gnome-es-base language-pack-kde-ca
0 paquets actualitzats, 0 instal·lats, 18 a suprimir i 5 a no actualitzar.
Es necessita obtenir 0B/3078kB d'arxius. Després del desempaquetat s'alliberaran 88,5MB.
No s'han trobat les dependències del paquets següents:
  j2re1.4-mozilla-plugin: Depén: j2re1.4 però no es pot instal·lar.
Resolving dependencies...
Les accions següents resoldran les dependències:

Suprimeix els següents paquets:
j2re1.4-mozilla-plugin

La puntuació és 119

Accepteu la solució? [Y/n/q/?]  

Encara no li he dit res...

Irene

---

### Post by papapep on 2008-02-28
uh! i on és el python?? No es deu dir així el paquet....

A veure, prova, si us plau, a fer:

```
sudo aptitude search python|grep i\ 
```
(atenció, hi ha [COLOR="Red"]**un **[/COLOR]espai en blanc després de la barra inclinada a l'esquerra)

i enganxa el que surti.

---

### Post by ipelegri6 on 2008-02-28
D'acord, però primer que li dic a la pregunta:

Accepteu la solució? [Y/n/q/?]  

quito?

---

### Post by papapep on 2008-02-28
"Quita", "quita" :-)

---

### Post by ipelegri6 on 2008-02-28
T'ho passo tot...

Accepteu la solució? [Y/n/q/?] q
S'estan abandonant les tasques per resoldre aquestes dependències.
Abandona.
irene@PELEGRI:~$ sudo aptitude search python|grep i\
[sudo] password for irene:
i   libpythonize0                   - Python packages to support KDE application
i   python                          - An interactive high-level object-oriented
i   python-apport                   - apport crash report handling library
i   python-apt                      - Python interface to libapt-pkg
p   python-at-spi                   - Assistive Technology Service Provider Inte
p   python-avahi                    - Python utility package for Avahi
i A python-cairo                    - Python bindings for the Cairo vector graph
i   python-central                  - register and build utility for Python pack
i   python-dbus                     - simple interprocess messaging system (Pyth
i A python-gconf                    - Python bindings for GConf2
p   python-genshi                   - python XML-based template engine
i A python-glade2                   - GTK+ bindings: Glade support
i A python-gnome2                   - Python bindings for the GNOME desktop envi
i A python-gnome2-desktop           - Python bindings for the GNOME desktop envi
i A python-gnomecanvas              - Python bindings for gnomecanvas (debug ext
i   python-gnupginterface           - Python interface to GnuPG (GPG)
i A python-gobject                  - Python bindings for the GObject library
i A python-gtk2                     - Python bindings for the GTK+ widget set
i A python-imaging                  - Python Imaging Library
i   python-kde3                     - KDE3 bindings for Python
p   python-kiwi                     - a graphical framework to construct simple
i   python-launchpad-bugs           - simple Python Interface to Bugs in Launchp
i A python-launchpad-integration    - library for launchpad integration
i A python-libxml2                  - Python bindings for the GNOME XML library
i   python-minimal                  - A minimal subset of the Python language (d
p   python-moinmoin                 - Python clone of WikiWiki - library
p   python-mpi                      - MPI module for Python
p   python-nifti                    - Python interface to the NIfTI I/O librarie
i A python-numeric                  - Numerical (matrix-oriented) Mathematics fo
p   python-ocempgui                 - graphical user interface toolkit providing
p   python-orca-brlapi              - python bindings for braille display access
i   python-problem-report           - python library to handle problem reports
p   python-pyatspi                  - Assistive Technology Service Provider Inte
p   python-pyfribidi                - FriBidi Python bindings
i A python-pyorbit                  - A Python language binding for the ORBit2 C
i   python-qt3                      - Qt3 bindings for Python
i   python-qt4                      - Python bindings for Qt4
i A python-qt4-dbus                 - DBus Support for PyQt4
p   python-scgi                     - Server-side implementation of the SCGI pro
p   python-simpy-gui                - python-based simulation package, GUI
i   python-sip4                     - Python/C++ bindings generator runtime libr
i   python-software-properties      - manage the repositories that you install s
i   python-support                  - automated rebuilding support for python mo
i   python-uno                      - Python interface for OpenOffice.org
p   python-wmi                      - DCOM/WMI client implementation, Python bin
i   python-xdg                      - A python library to access freedesktop.org
i A python-zopeinterface            - The implementation of interface definition
p   python-zsi                      - Zolera Soap Infrastructure
v   python2.4-at-spi                -
v   python2.4-avahi                 -
i   python2.4-exe                   - eLearning XHTML editor
v   python2.4-nifti                 -
v   python2.4-pyfribidi             -
v   python2.4-scgi                  -
v   python2.4-simpy-gui             -
i   python2.5                       - An interactive high-level object-oriented
v   python2.5-at-spi                -
v   python2.5-avahi                 -
i   python2.5-dev                   - Header files and a static library for Pyth
i   python2.5-minimal               - A minimal subset of the Python language (v
v   python2.5-nifti                 -
v   python2.5-ocempgui              -
v   python2.5-pyfribidi             -
v   python2.5-scgi                  -
v   python2.5-simpy-gui             -
p   vim-python                      - Vi IMproved - enhanced vi editor - with Py
irene@PELEGRI:~$   

Ara sí que ha trobat alguna cosa?

---

### Post by papapep on 2008-02-28
> i python2.4-exe - eLearning XHTML editor

Bé, he trobat una cosa que no m'esperava :-)

Potser el problema ve de que ja tens una versió anterior del paquet que intentes instal·lar...

Provem a treure'l:

```
sudo aptitude purge python2.4-exe
```

i després prova a instal·lar el pobre 2.5:

```
sudo dpkg -i python2.5-exe_1.03.0.3373-ubuntu1_i386.deb
```

---

### Post by ipelegri6 on 2008-02-28
Després de la primera ordre m'ha dit:

irene@PELEGRI:~$ sudo aptitude purge python2.4-exe
[sudo] password for irene:
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
S'està llegint la informació d'estat estesa
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
Els paquets següents contenen errors.
  j2re1.4-mozilla-plugin
Els paquets següents no s'utilitzen i se suprimiran:
  libavcodec0d libdc1394-13 libdvdcss2 libfame-0.9 libjack0.100.0-0
  libntfs-3g0 libpostproc0d libpostproc1d libpvm3 libswfdec0.3
  libtotem-plparser1 linux-headers-2.6.20-16
  linux-headers-2.6.20-16-generic mozilla-firefox-locale-es-ar
  mozilla-firefox-locale-es-es openoffice.org-l10n-es python-imaging
  python-zopeinterface transcode wspanish
Els paquets següents s'han apartat automàticament:
  language-pack-kde-ca-base language-pack-kde-es-base
Els paquets següents s'han apartat:
  language-pack-kde-en language-pack-kde-en-base language-pack-kde-es
Els paquets següents se suprimiran:
  python2.4-exe{p}
The following partially installed packages will be configured:
  language-pack-ca language-pack-ca-base language-pack-en
  language-pack-en-base language-pack-es language-pack-es-base
  language-pack-gnome-ca language-pack-gnome-ca-base language-pack-gnome-es
  language-pack-gnome-es-base language-pack-kde-ca
0 paquets actualitzats, 0 instal·lats, 21 a suprimir i 5 a no actualitzar.
Es necessita obtenir 0B/3078kB d'arxius. Després del desempaquetat s'alliberaran 126MB.
No s'han trobat les dependències del paquets següents:
  j2re1.4-mozilla-plugin: Depén: j2re1.4 però no es pot instal·lar.
Resolving dependencies...
Les accions següents resoldran les dependències:

Suprimeix els següents paquets:
j2re1.4-mozilla-plugin

La puntuació és 119

Accepteu la solució? [Y/n/q/?] 

Ara no quito? Em quedo amb Y?

---

### Post by papapep on 2008-02-28
Jo diria que sí (Y). Si algun dels paquets que ens carreguem et cal més tard, ja tenim la prova de quins eren aquí mateix al fòrum.

---

### Post by ipelegri6 on 2008-02-28
Oh-Oh, no troba alguna cosa...

Accepteu la solució? [Y/n/q/?] Y
Els paquets següents no s'utilitzen i se suprimiran:
  libavcodec0d libdc1394-13 libdvdcss2 libfame-0.9 libjack0.100.0-0
  libntfs-3g0 libpostproc0d libpostproc1d libpvm3 libswfdec0.3
  libtotem-plparser1 linux-headers-2.6.20-16
  linux-headers-2.6.20-16-generic mozilla-firefox-locale-es-ar
  mozilla-firefox-locale-es-es openoffice.org-l10n-es python-imaging
  python-zopeinterface transcode wspanish
Els paquets següents s'han apartat automàticament:
  language-pack-kde-ca-base language-pack-kde-es-base
Els paquets següents se suprimiran automàticament:
  j2re1.4-mozilla-plugin
Els paquets següents s'han apartat:
  language-pack-kde-en language-pack-kde-en-base language-pack-kde-es
Els paquets següents se suprimiran:
  j2re1.4-mozilla-plugin python2.4-exe{p}
The following partially installed packages will be configured:
  language-pack-ca language-pack-ca-base language-pack-en
  language-pack-en-base language-pack-es language-pack-es-base
  language-pack-gnome-ca language-pack-gnome-ca-base language-pack-gnome-es
  language-pack-gnome-es-base language-pack-kde-ca
0 paquets actualitzats, 0 instal·lats, 22 a suprimir i 5 a no actualitzar.
Es necessita obtenir 0B/3078kB d'arxius. Després del desempaquetat s'alliberaran 126MB.
Esteu segur de voler continuar? [Y/n/?] Y
S'està escrivint la informació d'estat estesa... Fet
(S'està llegint la base de dades ... hi ha 158668 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant j2re1.4-mozilla-plugin ...
(S'està llegint la base de dades ... hi ha 158665 fitxers i directoris instal·lats actualment.)
S'està preparant per a reemplaçar language-pack-kde-ca-base 1:7.10+20071012 (fent servir .../language-pack-kde-ca-base_1%3a7.10+20071012_all.deb) ...
S'està desempaquetant el reemplaçament de language-pack-kde-ca-base ...
(S'està llegint la base de dades ... hi ha 158664 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant libavcodec0d ...
S'està desinstal·lant libdc1394-13 ...
S'està desinstal·lant libdvdcss2 ...
S'està desinstal·lant transcode ...
S'està desinstal·lant libfame-0.9 ...
S'està desinstal·lant libjack0.100.0-0 ...
S'està desinstal·lant libntfs-3g0 ...
S'està desinstal·lant libpostproc0d ...
S'està desinstal·lant libpostproc1d ...
S'està desinstal·lant libpvm3 ...
S'està desinstal·lant libswfdec0.3 ...
S'està desinstal·lant libtotem-plparser1 ...
S'està desinstal·lant linux-headers-2.6.20-16-generic ...
S'està desinstal·lant linux-headers-2.6.20-16 ...
S'està desinstal·lant mozilla-firefox-locale-es-ar ...
S'està desinstal·lant mozilla-firefox-locale-es-es ...
S'està desinstal·lant openoffice.org-l10n-es ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(S'està llegint la base de dades ... hi ha 143785 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant python2.4-exe ...
(S'està llegint la base de dades ... hi ha 141520 fitxers i directoris instal·lats actualment.)
S'està desinstal·lant python-imaging ...
S'està desinstal·lant python-zopeinterface ...
S'està desinstal·lant wspanish ...
S'està configurant language-pack-gnome-ca (1:7.10+20080205) ...
S'està configurant language-pack-gnome-ca-base (1:7.10+20080205) ...

S'està configurant language-pack-gnome-es (1:7.10+20080205) ...
S'està configurant language-pack-gnome-es-base (1:7.10+20080205) ...

S'està configurant language-pack-kde-ca (1:7.10+20080205) ...
S'està configurant language-pack-kde-ca-base (1:7.10+20071012) ...

S'està configurant language-pack-ca (1:7.10+20080205) ...
S'està configurant language-pack-ca-base (1:7.10+20080205) ...
Generating locales...
  ca_AD.UTF-8... done
  ca_ES.UTF-8... done
  ca_ES.UTF-8@valencia... done
  ca_FR.UTF-8... done
  ca_IT.UTF-8... done
Generation complete.

S'està configurant language-pack-en (1:7.10+20080205) ...
S'està configurant language-pack-en-base (1:7.10+20080205) ...
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.

S'està configurant language-pack-es (1:7.10+20080205) ...
S'està configurant language-pack-es-base (1:7.10+20080205) ...
Generating locales...
  es_AR.UTF-8... done
  es_BO.UTF-8... done
  es_CL.UTF-8... done
  es_CO.UTF-8... done
  es_CR.UTF-8... done
  es_DO.UTF-8... done
  es_EC.UTF-8... done
  es_ES.UTF-8... done
  es_GT.UTF-8... done
  es_HN.UTF-8... done
  es_MX.UTF-8... done
  es_NI.UTF-8... done
  es_PA.UTF-8... done
  es_PE.UTF-8... done
  es_PR.UTF-8... done
  es_PY.UTF-8... done
  es_SV.UTF-8... done
  es_US.UTF-8... done
  es_UY.UTF-8... done
  es_VE.UTF-8... done
Generation complete.

S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
S'està llegint la informació d'estat estesa
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet
irene@PELEGRI:~$ sudo dpkg -i python2.5-exe_1.03.0.3373-ubuntu1_i386.deb
[sudo] password for irene:
dpkg: s'ha produït un error en processar python2.5-exe_1.03.0.3373-ubuntu1_i386.deb (--install):
 no es pot accedir a l'arxiu: No such file or directory
S'han trobat errors en processar:
 python2.5-exe_1.03.0.3373-ubuntu1_i386.deb
irene@PELEGRI:~$

---

### Post by papapep on 2008-02-28
hhehehe, si. Troba a faltar el paquet que li dius que instal·li :-D

No estàs al mateix directori que el fitxer que vols instal·lar (o el fitxer no hi és, que s'assembla molt).

---

### Post by ipelegri6 on 2008-02-28
I com el busco? On és? Com sé que el tinc?
Com veus, navego a un mar de dubtes de nou :confused:

---

### Post by ipelegri6 on 2008-02-28
L'he cercat amb el cercador del konkeror i no l'he trobat: sembla que no tinc el fitxer python2.5-exe_1.03.0.3373-ubuntu1_i386.deb

---

### Post by papapep on 2008-02-28
Cap problema. Fes un:

```
pwd
```

i et dirà a quin directori ets.

Si després fas:

```
ls -la
```

T'ensenyarà quins fitxers i directoris hi ha dins el directori on ets.

Si, per exemple, vols anar a l'escriptori (el tens allà?), fes:

```
cd /home/NOM_DEL_TEU_USUARI/Escriptori
```

Si ja ets on tens el fitxer, ja pots executar el "dpkg ...bla, bla, bla...".

Si així tampoc el trobes, fes:

```
sudo updatedb
```

Això actualitzarà la base de consulta de fitxers (pot ser que trigui una mica, no t'estranyis).

i ara:

```
locate python2.5-exe_1.03.0.3373-ubuntu1_i386.deb
```

i et dirà (si hi és) on és.

EDITO: Potser anirem més ràpids si el tornes a descarregar, que són dos segons.

---

### Post by ipelegri6 on 2008-02-28
je,je, ja l'he trobat. Però per què no l'he trobat fent la cerca amb el konkeror?

En fi, hi era però no s'ha deixat instal·lar:

irene@PELEGRI:/usr/bin/eXe$ ls
python2.5-exe_1.03.0.3373-ubuntu1_i386.deb
irene@PELEGRI:/usr/bin/eXe$ sudo dpkg -i python2.5-exe_1.03.0.3373-ubuntu1_i386.deb
(S'està llegint la base de dades ... hi ha 141345 fitxers i directoris instal·lats actualment.)
S'està desempaquetant python2.5-exe (de python2.5-exe_1.03.0.3373-ubuntu1_i386.deb) ...
dpkg: problemes de dependències impedeixen la configuració de python2.5-exe:
 python2.5-exe depèn de python-zopeinterface (>= 3.0.0-6); tot i així:
  El paquet python-zopeinterface no està instal·lat.
 python2.5-exe depèn de python-imaging; tot i així:
  El paquet python-imaging no està instal·lat.
dpkg: s'ha produït un error en processar python2.5-exe (--install):
 problemes de dependències - es deixa sense configurar
S'han trobat errors en processar:
 python2.5-exe
irene@PELEGRI:/usr/bin/eXe$

---

### Post by papapep on 2008-02-28
Fes:

```
sudo aptitude install python-zopeinterface python-imaging
```

Un cop fet això:

```
sudo dpkg --configure --pending
```

---

### Post by ipelegri6 on 2008-02-28
irene@PELEGRI:/usr/bin/eXe$ sudo aptitude install python-zopeinterface python-imaging
[sudo] password for irene:
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
S'està llegint la informació d'estat estesa
S'estan inicialitzant els estats dels paquets... Fet
S'està generant la base de dades de marcadors... Fet
Els paquets següents s'han apartat automàticament:
  language-pack-kde-ca-base language-pack-kde-es-base
Els paquets següents s'han apartat:
  language-pack-kde-en language-pack-kde-en-base language-pack-kde-es
Els paquets nous següents s'instal·laran:
  python-imaging python-zopeinterface
The following partially installed packages will be configured:
  python2.5-exe
0 paquets actualitzats, 2 instal·lats, 0 a suprimir i 5 a no actualitzar.
Es necessita obtenir 396kB/530kB d'arxius. Després del desempaquetat s'utilitzaran 1991kB.
S'està escrivint la informació d'estat estesa... Fet
Obté:1 [http://ad.archive.ubuntu.com](http://ad.archive.ubuntu.com) gutsy/main python-imaging 1.1.6-1 [396kB]
S'han recollit 396kB en 1s (237kB/s)
S'està seleccionant el paquet python-zopeinterface prèviament no seleccionat.
(S'està llegint la base de dades ... hi ha 143610 fitxers i directoris instal·lats actualment.)
S'està desempaquetant python-zopeinterface (de .../python-zopeinterface_3.3.1-3build2_i386.deb) ...
S'està seleccionant el paquet python-imaging prèviament no seleccionat.
S'està desempaquetant python-imaging (de .../python-imaging_1.1.6-1_i386.deb) ...
S'està configurant python-zopeinterface (3.3.1-3build2) ...

S'està configurant python-imaging (1.1.6-1) ...

S'està configurant python2.5-exe (1.03.0.3373-ubuntu1) ...
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències
Reading state information... Fet
S'està llegint la informació d'estat estesa
S'estan inicialitzant els estats dels paquets... Fet
S'està escrivint la informació d'estat estesa... Fet
S'està generant la base de dades de marcadors... Fet
irene@PELEGRI:/usr/bin/eXe$ sudo dpkg --configure --pending
irene@PELEGRI:/usr/bin/eXe$  

O sigui, que no hi ha res pending...

---

### Post by papapep on 2008-02-28
Ara busca al menu, hauries de tenir l'eXe per allà perdut :-)

---

### Post by ipelegri6 on 2008-02-28
Al menú no el trobo, i m'he portat dos ulls més perquè no se'm passi, fins i tot els he llegit en veu alta un per un. Res, no hi és a cap dels menús.
Com puc saber on està instal·lat o si ho està realment? I si faig un altF2 i li dic exe, funcionaria?

---

### Post by ipelegri6 on 2008-02-28
Ei, sí, ha funcionat! :):):):)
He fet AltF2 i exe i se m'ha obert el programa!!
Com ho haig de fer per posar-lo al menú? Vaig a editar i li dic que el comandament és "exe %u" ? (ho dic perquè com a firefox el comandament és "firefox %u" potser ha de ser igual)

---

### Post by ipelegri6 on 2008-02-28
També m'ha funcionat, ja el tinc al menú!!!

Moltes gràcies, papapep, encara no sé com però ja tinc l'eXelearning i en català!!

Ara a pel secondlife, però a un altre fil :):):)

I moltes gràcies!!!

---

### Post by papapep on 2008-02-28
Molt bé!!! M'alegro que hagi funcionat

Ara ja pots donar aquest "petit" fil per resolt :-)

---

### Post by ipelegri6 on 2008-03-02
Sí, sí, i tant, gràcies! Estic cercant com es posa com a resolt i no ho trobo. Què haig de fer?

---

### Post by ipelegri6 on 2008-03-02
Ja ho he trobat però no sé com posar una emoticona al costat del fil de discussió. Aquí ho deixo.
Fins aviat!!

---

### Post by lluisanunez on 2008-03-02
A dalt d'aquest fil, busca l'oció "Thread Tools"

---

