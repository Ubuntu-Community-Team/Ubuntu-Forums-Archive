---
title: "[SOLVED] Programes traductors,Ubuntu."
date: 2008-06-07
forum: Catalan Team
---

### Post by jaume69 on 2008-06-07
Hola,perquè no funciona cap traductor amb **Gnome** a **Ubuntu Hardy**?.tan un com en l'altre no puc traduir res(**Youtranslate,Gnome Translate**).

Com se "pillen". :mad:

---

### Post by SiscoGarcia on 2008-06-08
No sé què pretens traduir, però jo faig servir l'[apertium en línia]("http://xixona.dlsi.ua.es/apertium/ca/") i em tradueix bastant bé els textos i els webs.

---

### Post by jaume69 on 2008-06-09
Home,no està mal.lament el Apertium,però jo el que volia(com ja tenia a Gutsy,i a Hardy al principi em sembla que també)un traductor Anglès-Espanyol-Espanyol-Anglès. :confused:

---

### Post by ealbert on 2008-06-10
Hola, jo faig servir sovint el traductor de google:
"http://translate.google.es/translate_t"
i hem va força bé, pots traduir text i pàgines web

---

### Post by jaume69 on 2008-06-10
Si,pero quan no estàs a Internet i vols traduir algo tens que anar amb el **gTranslate** de **Firefox**.
No se perquè ho han tallat..¿?,el **Youtranslate**.
El **Gnome-translate** encara funciona,avuï,veig. :)

---

### Post by RainCT on 2008-06-11
No conec cap dels dos programes, però pel que sembla el Youtranslate necessita connexió a Internet per funcionar.

I en quant al teu missatge inicial, quin és exactament el problema amb que et trobes? Si no dones una mica més d'informació no sé com et podem ajudar...

---

### Post by jaume69 on 2008-06-11
[QUOTE="RainCT"]No conec cap dels dos programes, però pel que sembla el Youtranslate necessita connexió a Internet per funcionar.
[/QUOTE]

Si ambdós programes necessiten connexió a Internet,el **Gnome Translate** ja va bé però el **Youtranslate** no,encara que estiguis connectat.
Per això deia que potser han canviat el servidor o l'han tancat.¿¿??

[QUOTE="RainCT"]I en quant al teu missatge inicial, quin és exactament el problema amb que et trobes? Si no dones una mica més d'informació no sé com et podem ajudar...[/QUOTE]

El **YouTranslate** desde cónsola no dona cap error. 

:popcorn:

---

### Post by RainCT on 2008-06-11
Cert, a mi tampoc em funciona. M'estic mirant el codi font i pel que he vist fins ara com a mínim el servei de BabelFish està clar que no pot funcionar, perquè la pàgina ha canviat (ara és de Yahoo!), i el programa és de fa més d'un any així que és possible que la informació que té dels altres serveis tampoc valgui ja.

Actualització: Sip, pel que veig les dades que té de tots els motors fan referència a elements que ja no estan a les pàgines.

Actualització 2: Hi ha una versió nova; miraré a veure si amb aquesta funciona (i sinó provaré d'arreglar el problema jo mateix) i actualitzaré el paquet a l'Ubuntu.

---

### Post by jaume69 on 2008-06-11
On és el codi font?,a quina carpeta,arxiu.¿:)?

---

### Post by RainCT on 2008-06-11
Si tens els repositoris de codi activats, fes: apt-get source youtranslate

---

### Post by RainCT on 2008-06-12
He preparat un pegat per arreglar el programa i ara pujaré de la nova versió amb el pegat (i d'altres millores, com per exemple que ara té una entrada al menú) als dipòsits de l'Ubuntu Intrepid, on segurament demà ja estarà disponible per baixar.

Tinc previst arreglar també la versió de la Hardy però si vols pots utilitzar la [versió de la Intrepid](http://packages.ubuntu.com/intrepid/youtranslate) tan bon punt estigui disponible el paquet nou (versió: 1.1.10-0ubuntu1), en principi no hi hauria d'haver problemes encara que utilitzis la Hardy.

---

### Post by lluisanunez on 2008-06-12
Apertium va bé i és als repos, també de la Hardy

---

### Post by jaume69 on 2008-06-12
Doncs he instal.lat **Youtranslate** des de repositoris **Intrepid** i tampoc va...,igual que el de la pàgina de **[_l'autor_]("http://www.laas02.org/")**,que és la mateixa versió,tampoc va.

L'**Apertium** no el sé fer anar..(suposo que és des de cónsola)


**RainTC**:Jo no tinc mai els repositoris de codi Font,total 'pa' què..
I a part que ho faig per tenir el sistema més net. :confused:

---

### Post by RainCT on 2008-06-12
> **jaume69 said:**
> Doncs he instal.lat **Youtranslate** des de repositoris **Intrepid** i tampoc va...,igual que el de la pàgina de **[_l'autor_]("http://www.laas02.org/")**,que és la mateixa versió,tampoc va.

Si et fixes en el meu últim missatge, diu que l'agafis de la Intrepid tan bon punt hi arribi la versió arreglada (ara encara hi és l'antiga, la nova primer ha de ser compilada pels servidors d'Ubuntu).

La 1.1.10 (de la pàgina de l'autor) **no** funciona, però la que hi haurà a la Intrepid sí perquè li he afegit un pegat.

---

### Post by RainCT on 2008-06-12
Ja està, encara no ha arribat a packages.ubuntu.com però pots baixar la nova versió d'[aquí](http://launchpadlibrarian.net/15241928/youtranslate_1.1.10-0ubuntu2_all.deb).

---

### Post by jaume69 on 2008-06-13
Doncs ja funciona,gràcies Crack!! :)

---

### Post by eselma on 2008-06-13
Amb la Gutsy i anteriors havia usat QDacco, que és un diccionari resident, no un traductor; el tenies a ma i era molt ràpid. Ara, amb la Hardy i KDE 3.59 la versió dels repositoris no funciona; (no deixa escriure el text a la finestra), ni amb Compiz ni sense. Algú en té una pista, si us plau?

Mercès per endavant.

---

### Post by RainCT on 2008-06-13
@eselma: Vols dir que no és un problema de la teva insta&#320;lació? Jo el faig servir i em va perfectament...

---

### Post by eselma on 2008-06-13
Doncs he fet una purga del q/dacco i l'he tornat a instal·lar. Continua igual: no deixa entrar text a la barra, ni en la versió anglesa ni en la catalana. 

Uso [COLOR="Blue"]kubuntu hardy[/COLOR] de 32 bits. El QDacco dels repositoris és la versió 0.6d, i ara veig que l'autor és precisament en Carles Pina :-)

Potser al seu lloc web hi trobaré alguna idea. Mercès de tota manera.

---

### Post by orestesmas on 2008-06-14
Envia-li un missatge. Recentment ha estat modificant el qdacco, i és possible que hagis trobat un bug que caldrà comentar a l'autor...

---

### Post by eselma on 2008-06-15
Ja ho he fet, diu que ara s'ho mirarà. Com a usuari de [COLOR="Blue"]KDE[/COLOR], l'has provat i funciona?

Mercès de tota manera.

---

### Post by jaume69 on 2008-06-15
A mi també em funciona,però a [COLOR="DarkOrange"]Gnome[/COLOR].

-Inicia'l en el Terminal, :confused:

---

### Post by orestesmas on 2008-06-15
No l'he provat. No uso el qdacco habitualment. En algun cas puntual que l'he usat, ho he fet via la interfície web.

---

### Post by eselma on 2008-06-16
> **jaume69 said:**
> A mi també em funciona,però a [COLOR="DarkOrange"]Gnome[/COLOR].

-Inicia'l en el Terminal, :confused:

Si, és la primera cosa que faig, i no dóna cap pista; en el mode *debug* sembla que tampoc hi surt res d'anormal; ja l'hi he enviat a en Carles Pina. Ara s'ho està mirant.

Mercès en qualsevol cas.

---

### Post by madrigal_br on 2008-07-28
Vull un programa o interfase web per portuguès/català i català/portuguès.

Quin coneix?

---

