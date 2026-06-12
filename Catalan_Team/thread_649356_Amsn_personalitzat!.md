---
title: "Amsn personalitzat!"
date: 2007-12-24
forum: Catalan Team
---

### Post by patrickfromspain on 2007-12-24
Hola gent!

Fa uns dies va sortir, per fi, la versió estable de tcl/tk 8.5, el llenguatge de programació de l'amsn, amb suport d'antialiasing que fa que, per fi, l'amsn es vegi un programa decent i no com un de fa 10 anys.

He fet paquets tant de tcl tk com de la versió svn de l'amsn d'avui. Els paquets de TCL/TK 8.5 son un "backport" de debian sid i el de l'amsn l'he modificat per tant de que insta&#320;li algunes coses més (libsnack2, per poder enviar so que enregistrem pel micro i klash i cabextract, per poder veure els winks que ens enviin). A més, a nivell de configuració hi he canviat algunes cosetes i he afegit unes aparences que he fet jo (en blau-cel, verd i gris). 

He afegit un nou paquet: tcltls1.50. Esta compilat fent servir tcl8.5, d'aquesta manera a l'instal·lar-ho tot ja no demanarà l'instal·lació del tcl8.3 o 8.4.

Les versions de tcl/tk no molestaran amb versions anteriors, en canvi, l'amsn si que desinsta&#320;larà qualsevol versió anterior.

Primer insta&#320;leu el tcl8.5, després tk8.5 i finalment l'amsn.

**AVIS:** jo estic fent servir tot el que us passo i no he notat problemes. Si teniu prob lemes, haureu de tornar a la versió d'amsn que fèieu servir i només us podré ajudar si teníeu insta&#320;lat l'amsn dels repositoris oficials d'ubuntu. Si no n'esteu segurs de que fer, demaneu consell al sabis del fòrum xD.

Captura de pantalla:
[[IMG]http://img504.imageshack.us/img504/4348/amsncx8.th.png[/IMG]](http://img504.imageshack.us/my.php?image=amsncx8.png)

els links:

TCL8.5: [http://in.solit.us/archives/download/114664](http://in.solit.us/archives/download/114664)

TK8.5: [http://chronos.solit.us/archives/download/113979](http://chronos.solit.us/archives/download/113979)

AMSN 0.97 ESTABLE: [http://in.solit.us/archives/download/114530](http://in.solit.us/archives/download/114530)

TCLTLS1.50 [http://in.solit.us/archives/download/115681](http://in.solit.us/archives/download/115681)

SALUT!

EDITO: nova versio i espero que definitiva. ja no depen de klash, cabextract ni libsnack2. El connector de plugins no esta inicialitzat per defecte i no es fa servir la llibreria snack, sino aplay $sound. Ara també soporta drag and drop: arrastreu un arxiu a la conversa i aquest s'enviarà al vostre contacte.
EDITO: nova versio del tcl8.5
EDITO: afegit paquet tcltls1.50

---

### Post by lo gambusí on 2007-12-24
està molt bé!! :D

---

### Post by Joan Marc on 2007-12-25
Hola patrickfromspain,
Et vuldria comentar una cosa:
M'he descarregat els arxius que has penjat als anteriors links i com ja m'he trobat amb tots els paquets .deb que em vull instal·lar, que si són i386 no les puc instal·lar ja que em diu "Error: Wrong architecture i386", i només puc instal·lar els que són amd64.
Cal dir que vaig proposar aquest problema al fòrum, i que la solució que em van donar ve ser que fes servir el Synaptic per buscar els paquets i que no ho fes pel meu compte.
Bé, estaria molt agraït si poguessis penjar les versions amd64, o si em poguessis dir alguna solució al meu problema.

Moltíssimes gràcies!

---

### Post by patrickfromspain on 2007-12-25
la solucio al teu problema seria compilar els paquets font i, en comptes de crear un deb, els insta&#320;les tal cual.
Aqui tens instruccions de com fer-ho:
[http://ubuntuforums.org/showthread.php?t=535176](http://ubuntuforums.org/showthread.php?t=535176)

Si tens cap dubte.. pregunta, tu mateix

salut

---

### Post by Joan Marc on 2007-12-25
patrickfromspain, tot m'anaba bé, fins que he arrivat a:
> Per facilitat a l'hora de treballar, descomprimiu tot a l'escriptori. Comencem, en un terminal:

cd ~/Desktop/tcl8.5.0/unix
./configure --prefix=/usr/local
make
sudo make install
sudo ln -s /usr/local/bin/tclsh8.5 /usr/local/bin/tclsh

M'ha sortit el següent des del terminal:
```
gami@Gami:~$ cd ~/Desktop/tcl8.5.0/unix
bash: cd: /home/gami/Desktop/tcl8.5.0/unix: No such file or directory
gami@Gami:~$ ./configure --prefix=/usr/local
bash: ./configure: No such file or directory
gami@Gami:~$ make
make: *** No rule to make target `Makefile.PL', needed by `Makefile'.  Stop.
gami@Gami:~$ sudo make install
make: *** No rule to make target `Makefile.PL', needed by `Makefile'.  Stop.
gami@Gami:~$ sudo ln -s /usr/local/bin/tclsh8.5 /usr/local/bin/tclsh

```

Gràcies.

---

### Post by patrickfromspain on 2007-12-25
on has descarregat els paquets que t'has baixat? on els has descomprimit? Si es a l'escriptori, igual has de ver cd ~/Escriptori/tcl8.5.0/unix, perdo. si no, has de fer cd a on tinguis la carpeta tcl8.5.0

salut!

---

### Post by Joan Marc on 2007-12-25
També ho havia pensat, però ho tinc descarregat i descomprimit a home/gami/Desktop.

Gràcies.

---

### Post by patrickfromspain on 2007-12-25
be, doncs mira que la carpeta es digui tcl8.5.0 i no d'alguna altra manera, mes no se m'acut!

---

### Post by patrickfromspain on 2007-12-28
actualitzat a l'ultima versio estable!

---

### Post by kukat on 2007-12-30
Gràcies! A mi m'ha funcionat de meravella!!! 
Molt més bonic que el de Guindows.!!!:)

---

### Post by lluisalguero on 2007-12-30
Mirant per altres webs, vaig sentir parlar del aMSN. Fins ara feia servir el Pidgin però no m'acababa de convençer.

L'he instalat i he vist que hi ha caràcters que no es escriu bé (accents, apòstros i tal).

Es per això que he fet una cerca al fòrum i he trobat aquest post. No sé si haig de seguir les pases que s'indiquen al principi del post o no cal. La versió que tinc ara instalada és la 0.97b.

Això dels caràcters, que pot ser?

Gràcies per la vostra ajuda

---

### Post by patrickfromspain on 2007-12-30
si la versio de l'amsn que tens es la dels repositoris, la pots desinsta&#320;lar i pots baixar-te i insta&#320;lar els 3 paquets que he penjat: insta&#320;la primer el tcl8.5, despres tk8.5 i per ultim l'amsn.

Si segueixes tenint problemes amb els caràcters, en parlem i mirarem més a fons d'on pot venir.

salut!

---

### Post by lluisalguero on 2007-12-30
> **patrickfromspain said:**
> si la versio de l'amsn que tens es la dels repositoris, la pots desinsta&#320;lar i pots baixar-te i insta&#320;lar els 3 paquets que he penjat: insta&#320;la primer el tcl8.5, despres tk8.5 i per ultim l'amsn.

Si segueixes tenint problemes amb els caràcters, en parlem i mirarem més a fons d'on pot venir.

salut!

Si, la versió que tinc és la dels repositoris. Faré això que em dius i us dic com ha anat...fins ara !!!

---

### Post by lluisalguero on 2007-12-30
> **patrickfromspain said:**
> si la versio de l'amsn que tens es la dels repositoris, la pots desinsta&#320;lar i pots baixar-te i insta&#320;lar els 3 paquets que he penjat: insta&#320;la primer el tcl8.5, despres tk8.5 i per ultim l'amsn.

Si segueixes tenint problemes amb els caràcters, en parlem i mirarem més a fons d'on pot venir.

salut!

Instal·lat de nou i en perfecte funcionament, ara els caràcters es veuen tots bé...gràcies patrick

---

### Post by Joan Marc on 2007-12-30
Hola patrick,
Ja he solucionat la instal·lació, nomès he hagut de canviar Desktop per Escriptori.
El problema que tinc ara és a l'iniciar la sessió, en que em diu que fa falta que m'instal·li una "cosa" perquè es pugui connectar, el cas és que encara que ho instal·li, continua dient-me que no està instal·lat, això que ho he provat amb totes les possiblitats...

Gràcies!

---

### Post by patrickfromspain on 2007-12-30
sudo apt-get install tcltls

---

### Post by Joan Marc on 2007-12-31
Res, em diu que el tcltls ja es troba en la versió més recent i l'amsn continua dient que no està instal·lat.

BON ANY!

---

### Post by patrickfromspain on 2008-01-04
proba d'instal·lar la nova versio de tcltls que he instalat, igual et funciona. salut!

[http://in.solit.us/archives/download/115681](http://in.solit.us/archives/download/115681)

---

### Post by Joan Marc on 2008-01-06
És per 32 bits...xD
Bé, treuré el de 64 bits i posaré el de 32, ja et dire si m'ha anat bé o no!

Gràcies!

---

### Post by patrickfromspain on 2008-01-06
ei, espera!

gksudo gedit /usr/lib/tls1.50 i mira si hi posa package ifneeded 1.5 

Si hi posa 1.5 hi has de posar 1.50. Despres, a l'amsn, ves prefrencies altres o avançades (es la ultima pestanya) i alla a tls hi poses: /usr/lib/tls1.50

A vere si aixi va

salut!

---

### Post by eduardsola on 2008-01-06
> **patrickfromspain said:**
> si la versio de l'amsn que tens es la dels repositoris, la pots desinsta&#320;lar i pots baixar-te i insta&#320;lar els 3 paquets que he penjat: insta&#320;la primer el tcl8.5, despres tk8.5 i per ultim l'amsn.

Si segueixes tenint problemes amb els caràcters, en parlem i mirarem més a fons d'on pot venir.

salut!

He fet el que dius, i em continua mostrant els caracters fatal, no posa els accents ni mostra les ç...

He provat amb la codificació, he provat amb l'Automatic i l'ascii, n'hi ha un munt i no sé quina posar...

Què faig?

---

### Post by patrickfromspain on 2008-01-06
Sembla que tens problemes amb la localitzacio. El primer que pots provar es, en un terminal: sudo locale-gen --purge

Llavors reinicia l'amsn, i a veure que tal va. Si segueixes tenint el problema, ves a Sistema -> Administració -> Support d'idioma i assegura't que tens posat el Catalan (Spain). Si tens posat el d'andorra o qualsevol altre, canvia'l i reinicia el pc. A veure si va. Si aixo no serveix.. torna aqui i seguire'm mirant de solucionar-ho.

salut!

---

### Post by Joan Marc on 2008-01-06
Hola Patrick,
He fet el que m'has dit, però em surt un error que t'adjunto.

Gràcies

---

### Post by patrickfromspain on 2008-01-06
estic a la parra... era gksudo gedit /usr/lib/tls1.50/pkgIndex.tcl

---

### Post by Joan Marc on 2008-01-06
> **patrickfromspain said:**
> 
Si hi posa 1.5 hi has de posar 1.50. Despres, a l'amsn, ves prefrencies altres o avançades (es la ultima pestanya) i alla a tls hi poses: /usr/lib/tls1.50

Ja ho tenia a 150, i no a 1.5.
Pero he posat allo al aMSN i ja ha iniciat la sessió!
El que trobo és que no hi veig gaire diferència, vull dir que s'assembla al screenshoot que tens al primer post, pero no és ven bé igual.

Gràcies!

---

### Post by patrickfromspain on 2008-01-07
A l'amsn, ves a preferencies i alla a la pestanya d'aparença. Posa canviar la font i posa una Sans (10 o 11 està bé), ja que hem sembla que la font per defecte es Helvetica, que es veu malament igual. Per a que faci hauras de reiniciar l'amsn.

salut!

---

### Post by eduardsola on 2008-01-07
Ja està solucionat, ho he fet mitjançant el suport d'idioma, no estava del tot instal·lat i per això no se'm veien les ç ni els accents...


Gràcies!

---

### Post by Joan Marc on 2008-01-08
No em referia a la lletra, sinó a la aparença en general, mira't les captures.

Gràcies :)

---

### Post by patrickfromspain on 2008-01-08
aaah es clar.. no tens les meves pells... baixa't el meu paquet d'amsn i descomprimeix-lo (boto dret, extreu aqui). Alla hi tindras 2 arxius més. Descomprimeix el que hi diu data i ves buscant la carpeta skins. Alla hi seran les meves: copiales a ~/.amsn/skins

salut!

---

### Post by Joan Marc on 2008-01-08
Les he intentat copiar a /usr/local/share/amsn/skins, però em diu que no tinc permís per escriure a la carpeta.

---

### Post by patrickfromspain on 2008-01-08
copiales al teu home, sota .amsn/skins

---

### Post by Joan Marc on 2008-01-08
Ostres la carpeta era oculta, no hi havia caigut!!
Està molt bé!! 
Moltes gràcies patrick!!:D.

PD: No existeix pas una ampliació per l'amsn (com el messenger plus) per veure els diferents colors dels contactes, guardar converses...?? És nomès per saber-ho!

---

### Post by patrickfromspain on 2008-01-08
a la carpeta plugins del paquet hi havia el Colored Nicks ;)

---

### Post by pespin on 2008-01-08
Hi ha un plugin que es diu amsn plus, i per guardar les converses... es guarden soles ja. A la finestra de Preferencies hi ha una pestanya on pots configurar-ho :)

---

### Post by Joan Marc on 2008-01-08
Patrick, nomès em queda dir-te que ets una màquina :D!! Moltes gràcies!!.

pespin, des d'on es pot baixar l'amsn plus?

Gràcies a tots!! :)

---

### Post by Joan Marc on 2008-01-10
Ja le trobat!
Una cosa, encara no funcionen els colors de fons dels niks no?

Merci!

---

### Post by pespin on 2008-01-10
Que jo sàpiga encara no funciona no

---

### Post by Joan Marc on 2008-01-10
OK! Gràcies!

---

### Post by eduardsola on 2008-01-11
esborrar missatge xD

---

