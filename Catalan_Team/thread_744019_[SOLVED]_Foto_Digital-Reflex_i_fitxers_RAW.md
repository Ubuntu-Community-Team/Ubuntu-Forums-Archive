---
title: "[SOLVED] Foto Digital-Reflex i fitxers RAW"
date: 2008-04-02
forum: Catalan Team
---

### Post by prostata on 2008-04-02
Em sabriau dir si Ubuntu porta algun programari que tracti imatges RAW?? i si no és pas així, ¿com podria fer-lo?....gràcies

---

### Post by prostata on 2008-04-02
Disculpeu però m'he precipitat ja que cercant per Sant google he vist que digikam és als repos, i encara que jo treballo amb genome tractaré de fer proves amb ell ja que ignoro si per genome hi ha res que funcioni...

---

### Post by CarlesOriol on 2008-04-02
Un format d'imatge raw vol dir sols dades sense estructura tal com "arriben s'enregistren".

Per exemple pot ser una llista de punts en rgb o rgba o bits en blanc i negre sense cap tipus de compressió ni de identificació.
Però un raw també pot ser un fluxe de video en format mpeg o dades d'audio ...

Així que el raw "a seques" no t'identifica res.

----------------------

Edito: El titol del post "format raw" és un oximoron.

---

### Post by lluisalguero on 2008-04-02
Tens el Ufraw, encara que jo després de provar-lo, malauradament, em quedo amb els programes de windows....que hi farem !!!

---

### Post by papapep on 2008-04-02
L'[UFRaw]("http://www.networkgulf.com/content/view/199/265/") també existeix com a afegit pel Gimp, amb el qual després pots fer el que et plagui amb la imatge. No sé què fa o deixa de fer com a aplicació "standalone", però per importar-lo al Gimp va molt bé.

---

### Post by orestesmas on 2008-04-03
> **prostata said:**
> ...ja que ignoro si per genome hi ha res que funcioni...

Home, aquesta és bona!! Podria reblar el clau, però avui estic magnànim i m'abstindré :)

---

### Post by prostata on 2008-04-03
> **orestesmas said:**
> Home, aquesta és bona!! Podria reblar el clau, però avui estic magnànim i m'abstindré :)


Per un casual....et vols referir a GQview????

---

### Post by prostata on 2008-04-03
Em permeto obrir aquest fil doncs penso que encara que hi poden haver altres llocs per tractar aquestos temes, qui hi son, és probable que alguns de nosaltres tinguem en comú la foto i més concretament la foto-digital-reflex.

Jo us presento la meva situació per si familiar o coneguda per algú de vosaltres:

La meva màquina és una Olympus E-410 amb dues òptiques, 10Mpixels i res més d'important.
El format que estic probant es RAW però l'imatge apareix a l'ordinador en format .ORF
He tractat d'obrir l'imatge  tant amb digikam, com gqview, UFraw, però en tot cas sempre em diu que el format no es soportat.
Am la màquina be un soft per a windows i mac, però jo vull fer-lo amb ubuntu..

Quins procediments, plugins o demés estris hauria de fer servir per treballar aquests formats amb el meu ubuntu??

---

### Post by ffp on 2008-04-03
Hola prostata,

Jo tinc una Olympus, d'un altre model, i el format raw (.orf)  l'obro perfectament, no recordo que vaig fer, crec que tinc apunts a casa, quan arribi te'ls diré.
Per cert, no pots editar amb gimp, o bé no els pots obrir amb el visualitzador ?
Cal tenir en compte que el format raw no es un standard, cada marca fa el seu !

---

### Post by jmaspons on 2008-04-03
Hola,
Em sembla que depèn del format de cada marca. Per Nikon cal instal·lar un paquet que es troba als repositoris d'ubuntu i que es diu denef, per exemple.

Salut!

---

### Post by papapep on 2008-04-03
Próstata, hi ha un programa que es diu [Dcraw]("http://cybercom.net/~dcoffin/dcraw/") que, entre moltes altres, diu que importa els raw de la teva càmara al Gimp:

> # rawphoto.c -- basic plugin for GIMP 1.2 & 2.0
After installing "dcraw", do "gimptool --install rawphoto.c". My plugin provides a simple dialog box for loading raw files into the Gimp. Udi Fuchs and Joseph Heled have written much nicer plugins, with live preview, histograms, and color curves.


Per cert, el Dcraw [és als repositoris oficials]("http://packages.ubuntu.com/search?keywords=dcraw&searchon=names&suite=gutsy&section=all"), no cal fer cap invent per instal·lar-lo.

---

### Post by papapep on 2008-04-03
Próstata, has duplicat la temàtica amb el dels fitxers RAW.

---

### Post by CarlesOriol on 2008-04-03
Si... jo tampoc entenc perque aquest fil seguies aquí.

Prostata: per què no fas una foto qualsevol i ens la penges algun lloc per veure-ho?

Per cert una imatge en format raw de 10 Mpixels ha d'ocupar (amb un rgb de 24 bits - 1 byte per color - ) 30 Mbytes...

---

### Post by prostata on 2008-04-03
És cert hi obert un fil nou amb temàtica similar, però la meva intenció és enfocar-lo fonamentalment cap a la foto-imatge, com a temàtica. Crec que és força més ampli i més especific. De totes totes si considereu que amb un fil, l'anterior, ja ni ha prou, doncs val, cap problema, elimineu un dels dos i....jo per part meva i si us sembla bé el que faig ara mateix o posar el solved a l'altre fil

salutacions

---

### Post by prostata on 2008-04-03
> **papapep said:**
> Próstata, hi ha un programa que es diu [Dcraw]("http://cybercom.net/~dcoffin/dcraw/") que, entre moltes altres, diu que importa els raw de la teva càmara al Gimp:



Per cert, el Dcraw [és als repositoris oficials]("http://packages.ubuntu.com/search?keywords=dcraw&searchon=names&suite=gutsy&section=all"), no cal fer cap invent per instal·lar-lo.

Gràcies papapep ja ho tinc instal-lat, però encara dona error quan obro en format ORF, però ja ho intentaré i el resultat que hi hagi ho expressaré al altre fil...
salutacions

---

### Post by ffp on 2008-04-03
Prostata,

Saltant de l'altre fil, efectivament el plugin per gimp que em funciona be per els raw d'Olympus es el DCRaw.
Si t'agrada la fotografia et recomano el Hugin per fer panorames i amb el plugin enblend pots forsar la fussió de panoramas (en format tiff)

---

### Post by CarlesOriol on 2008-04-03
ok. però penja una foto per veure el problema.

---

### Post by papapep on 2008-04-03
> però encara dona error quan obro en format ORF

On m'he perdut?? No parlaves dels RAW??? Quin embolic tot plegat...

---

### Post by ffp on 2008-04-04
Papapep,

Fitxers raw => extensió .orf !. EDITO: En les màquines Olympus.

---

### Post by CarlesOriol on 2008-04-04
Prostata:

Em flipa que demanis ajuda a la llista si despres no fas el que et demanem per ajudar-te.

---

### Post by papapep on 2008-04-04
> **ffp said:**
> Papapep,

Fitxers raw => extensió .orf !

Ja ho he trobat: és el nom que li dóna Olympus als seus RAW.  [Cada marca li dóna el nom que li surt dels nassos]("http://en.wikipedia.org/wiki/RAW_image_format").

---

### Post by prostata on 2008-04-04
> **CarlesOriol said:**
> Prostata:

Em flipa que demanis ajuda a la llista si despres no fas el que et demanem per ajudar-te.

Haveure Carles, tranquilitzat i calmat, en aquest cas concretament la meva capacitat de resposta no es directament proporcional a la teva velocitat o necessita de resposta. 

No tinc plena diponibilitat de temps per estar pendent del fòrum.
No tinc plena disponibilitat de temps per fer el que en aquest cas tu, em demanes, malgrat agrair-te el teu interes.

Mol sovint jo també he flipat en veure les teves respostes generals i sobre tot la actitud que algunes han mostrat, és dir el que hi ha a sota l'escriptura gràfica, i sempre he estat respectuos, ¿no?

no cal que flipis, Carles, el que em permeto recomenar-te, és una mica de empatia, no més i si decas una mica més de comprensió cap a les situacions de les persones que aquí venim, no cal que flipis, no tens cap mena de necessitat ni cap motiu.

salutacions

---

### Post by prostata on 2008-04-04
Gràcies per la vostra ajuda, a tots.

---

### Post by papapep on 2008-04-04
Que tanquis el fil significa que ja et funciona correctament?

---

### Post by prostata on 2008-04-04
papapep;

vol dir que funciona correctament però en windows
en ubuntu és excessivament complicat, ja veus tot el que s'ha creat però continuo sense poder fer-lo anar.

De fet jo he intentat prioritariament treballar aquest tema en entorn Ubuntu, no m'agrada estar canviant d'un sistema a altre, però sempre he tingut molt clar que agafaré d'ells tot el que em convingui, i en aquest cas windows no em presenta cap problema, cap afegit, cap plugin, és dir com una seda. En ubuntu estic tenint més "incidències" de les que puc atendre, per tant continuaré provant de trobar una sol-lució a aquest tema en ubuntu, però mentre no sigui així, la resta de la feina en formats .orf ho faré amb l'altre. dono les gràcies a tots per les seves aportacións, però, jo no he fet ni faré una creuada ni en contra ni a favor, ja no tinc ni ganes ni temps ni desitjos de qüestionar un S.O. contra altre, els dos son bons o si més no tant útils un com l'altre, i parlo d'utilitat, i en aquest cas parlo com a usuari, no com a cientìfic, ni com a profe. ni com res rel-lacionat amb la docència i la investigació, si no com a simple usuari, no em plantejo el que corre per sota del programari per veure un determinat format d'imatge, no en aquest cas, ja que com a usuari el que li demano ara, en aquest context, al programari és que em sol-lucioni la qüestió, no una lecció magistral sobre "el com ho fa". 

Salutacions

---

### Post by papapep on 2008-04-04
Doncs així no és SOLVED. Ho trec. De la resta no et comento res, ja ho has dit repetits cops i ja ho tinc clar.

---

### Post by prostata on 2008-04-04
> **papapep said:**
> Doncs així no és SOLVED. Ho trec. De la resta no et comento res, ja ho has dit repetits cops i ja ho tinc clar.

benvolgut papapep:

si tu administres la llista, és evident que tens el poder de fer el que creguis amb els posts. ara bé, entenc que el fil és obra meva i entenc a més que per a mi aquest fil resta tancat, ja que no hi han sol-lucions ni en el temps ni en la forma. jo el tornaré a SOLVED perquè per a mi està tancat, i tu faràs el que creguis més oportú pel manteniment de la llista.

---

### Post by papapep on 2008-04-04
Jo no el tornaré a obrir per que ara no ens posarem a jugar com a nens a obrir i tancar, però SOLVED significa solucionat i aquest tema no ho ha estat degudament. A partir d'aquí fes el que et sembli adient.

---

### Post by prostata on 2008-04-04
Com dius aquest tema no ha estat solucionat adequadament, voldria veure com acaba, un final feliç, i com que jo no soc un infant i tu tan poc, doncs restarà obert el fil, fins que tot acabi bé o per avorriment, la qual cosa evidentment, no desitjo, es clar.
salutacions

---

### Post by CarlesOriol on 2008-04-04
1er - Tu a mi no m'has de recomanar res.

2on -  Fas una pregunta per que algú altruistament t'ajudi i després desprecies a qui et vol ajudar, les seves ganes i el seu temps. I per cert m'apasiona el tema dels formats gràfics, he treballat molts anys (quan era programador de veritat :-) ) i probablement t'hagués tret una solució fàcil. Però tu això to has passat pel forro. 

3er -  Si mires el contingut del que t'he enviat ha estat força didactic per sota de la forma. I si fas un esforç veuras que ho acostumen a ser quan algú em demana ajuda i puc fer-ho.

4rt - Per mi un fil que acaba amb una recomanació d'usar windows per cansansi em sembla que no està tancat ni de bon tros.  

5è - Puc respectar a d'altres usuaris del fòrum com en patrickfromspain amb qui més d'un cop hem discutit (normalment sobre el perquè de tot plegat i llicències), però que fan una feinada increible i és un plaer aprendre de les seves respostes... 

Si algú té interés en poder llegir aquest format jo estic disposat a seguir-ne parlant.
----------------------------------
Edito: seguir-ne parlant... en un altre fil, aquest ja m'ha cansat.

---

### Post by prostata on 2008-04-10
Ja sé perquè no em funcionava UFRaw al moment d'obrir els arxius ORF,la qüestió rau en que la versió de UFRaw que incorpora els respos de Gutsy, és un pel antiga, no més cal descarregar-se la versió UFRaw 0.13 i tot arreglat

---

