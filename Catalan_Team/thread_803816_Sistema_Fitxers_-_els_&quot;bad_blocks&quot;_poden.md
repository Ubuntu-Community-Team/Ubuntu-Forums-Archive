---
title: "Sistema Fitxers - els &quot;bad blocks&quot; poden ser recuperables?"
date: 2008-05-22
forum: Catalan Team
---

### Post by tacubuntuforums on 2008-05-22
Hola:
Últimament he tingut que apagar sovint un PC per la via dràstica per algun problema de hardrware que el deixa totalment congelat o, a vegades, no em permet executar cap programa nou (encara no sé a què es degut, amb Windos: pantallazo azul).

Explico amb el detall que recordo lo que m'ha passat recentment (què no sé si ha sigut provocat per aquestes apagages forçades) però no us fixeu massa, no crec que els detalls siguin importants. Lo que vull resoldre està al final.

Ahir, al arrencar-lo vaig trobar que durant l'engegada, al fer la revisió de la partició /home, el programa FSCK va trobar errors _d'inconsistència_.

Va trobar tres inòdes que compartien entre ells alguns blocs del sistema de fitxers tipus ext3.
Dos dels arxius (corresponents a aquests inodes) eran de la Cache del Firefox i de la paperera de la Cache del firefox (dins la carpeta personal d'un usuari). L'altre no ho sé perquè el programa FSCK va parar, amb estatus d'error=4, abans d'informar, però jo he suposat que seria també de la mateixa Cache.

Vaig poder entrar, de totes maneres, al sistema amb la conte de l'usuari i el seu escriptori gràfic. Com que al esborrar la Cache amb el Firefox continuaven existint aquests arxius problemàtics, a la brava, em vaig carregar tota una carpeta dins la paperera de la cache. No recordo exactament quina pero l'arbre era mes o menys així:


```
.mozilla/firefox/yfgnip9h.default/

|-- Cache
|-- Cache.Trash
|    |-- Trash
|          |-- Cache
|    |-- Trash-1
|          |-- Cache
```


Ara ja s'ha refet i només hi-ha una Cache (sense paperera)

La questió es que el problema no es va solventar al esborrar, a pel, aquella carpeta. Em sembla que Les inconsistències van fer que no pogués obrir bé el Firefox i van posar la partició en RO (read only).

Vaig sortir, l'apagada amb **SHUTDOWN -F** no va arribar fins al final. I vaig tenir que apagar amb el botó d'apagar (botonazo)

Al engegar un altre cop vaig entrar al manteniment i vaig demanar al sistema fer **e2fsck** interactiu. A la pregunta de si duplicar els blocs compartits vaig dir SI i a la pregunta de si esborrar el fitxer vaig dir NO, a la resta de preguntes sobre la comptabilitat de blocs vaig respondre que SI.

Al entrar al escriptori grafic, Firefox s'engegaba bé i al fer **dumpe2fs** a la llista de "bad blocks" sortia el 1600 només.

Vaig tornar a engegar i entrar a les tasques administratives; després de fer **fsck -c -c** (dues vegades -c) i no recordo que més, vaig trobar que la llista de blocks defectuosos havia canviat a 1664,1912 (!)
El sistema em deia que tornava a haver blocks compartits entre dos inodes: el del journaling system (del sistema de fitxers ext3) i l'inode de bad-blocks.

Vaig tornar a executar **e2fsck** i, com que no vaig voler esborrar cap dels dos inodes (ningú m'assegurava que el sistema els refaria), vaig respondre que Sí volia duplicar el blocs i NO esborrar els fitxers i SI a la resta de preguntes sobre comptabilitat de blocs.

[COLOR="DarkRed"]Ara **dumpe2fs** dona  la llista de bad-blocks: 1664,1912
però jo crec que no deuen estar mal físicament. Llavors vull saber com puc saber si això es així, si els puc recuperar a la llista de blocs lliures i com.[/COLOR]

Gràcies

---

### Post by papapep on 2008-05-22
> Ara dumpe2fs dona la llista de bad-blocks: 1664,1912
però jo crec que no deuen estar mal físicament

I perquè creus això? Quin fet objectiu t'hi porta?

> Llavors vull saber com puc saber si els blocs estan bé físicament, si els puc recuperar a la llista de blocs lliures i com.

Si estiguessin bé físicament el fsck ja els hauria recuperat, ja que seria un "simple" error lògic al haver-se tancat el sistema de fitxers de manera "no convencional". Si tot i fer la verificació et segueixen sortint marcats com a dolents, porta directament a pensar que és un error físic real.
Els casos que he tingut d'aquests tipus els he aclarit (per saber definitivament si el problema era físic o no) utilitzant alguna de les utilitats que els fabricants de discs durs proporcionen per a efectuar aquest tipus de comprovacions.

Aquí pots trobar les de Seagate/Maxtor: [http://www.seagate.com/www/en-us/support/downloads/](http://www.seagate.com/www/en-us/support/downloads/)

si el teu disc és d'una altra marca hauràs de mirar si el fabricant en té i les proporciona.

Per cert, aquí et passo un parell d'enllaços molt interessants sobre com actuar en efectuar una recuperació de dades en cas de desastre i casos similars:

[http://eduunix.ccut.edu.cn/index/html/linux/OReilly.Linux.Server.Hacks.Volume.Two.Dec.2005/0596100825/morelnxsvrhks-CHP-10-SECT-7.html](http://eduunix.ccut.edu.cn/index/html/linux/OReilly.Linux.Server.Hacks.Volume.Two.Dec.2005/0596100825/morelnxsvrhks-CHP-10-SECT-7.html)

[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)

---

### Post by tacubuntuforums on 2008-05-22
De moment gràcies, Pep. Ja m'ho miraré (no tinc cap problema amb l'anglès).

Em sembla recordar que aquest disc es Seagate (com saber-ho des de Linux sense obrir la caixa?)

Jo he pensat que potser els blocs no eren defectuosos perquè primer em sortia el 1600 i després aquests altres dos:1664 i 1912, només. A més vaig pensar que potser per haver contestat SI a fer la duplicació va fer que continuessin allí. Però, vaja, només ho crec perquè no se com treballa el programa i el manual no cobreix tants detalls en les explicacions (i ho comprenc), com per ex.: no diu si la llista de bad blocs o el journal es refan (quan o com) si s'esborra el seu inode.

També crec que si estan malament físicament deu ser per tantes (ja deuen ser unes 50) apagades amb "botonàs", que procuro fer-les quan no es llegeix el disc dur. A vegades, quan es queda penjat continua llegint el disc a intervals més o menys periódocs i, sempre procuro apagar passat el màxim tems possible des de l'ultima lectura que sol ser entre 5 i 10 segons. Tu que creus? Com ho veus?

---

### Post by papapep on 2008-05-23
> Em sembla recordar que aquest disc es Seagate (com saber-ho des de Linux sense obrir la caixa?)

Ho pots trobar fent un (tria el tipus de disc que quadri amb el teu):

```
dmesg|grep ide|ata|sata
```

així t'hauria de sortir, entre d'altres, alguna línia on surti el model de disc, i així pots buscar (si no és clar ja pel nom) quin és el fabricant.
En el cas del meu portàtil, fent:

```
dmesg|grep ata
```

em surt "HTS541060G9AT00", que buscat a Google (tot i que la "H" inicial ja és indicativa) em diu que és un [Hitachi de 60 Gb]("http://computers.pricegrabber.com/hard-drives/m/11344022/").

> Tu que creus? Com ho veus? 

Doncs no sé. Em demanes un diagnòstic sense poder veure "el malalt".
Jo faria la verificació que t'he comentat abans i, si a nivell físic està bé, tornaria a fer el fsck i li diria que arreglés els inodes com a ell li sembli (pel que comentaves només són dades de la memòria cau del Firefox, oi?). En teoria això t'ho hauria de deixar solventat el tema.

---

### Post by tacubuntuforums on 2008-05-23
Just després d'escriure't vaig trobar aquest comando per tenir info dels discs:
/sbin/discover --model disk
/sbin/discover --vendor disk
 
No entenc perque no puc fer servir mes de dues d'aquestes opcions an una mateixa instrucció
 
Ja estic fent servir un windos, a punt de baixarme un .exe per instalar la versió DOS (crec es més convenient) de la utilitat de discos de Seagate. El pasaré ja només per saber que pasa; perquè segons lo que dius si es podesin recuperar aquells blocs, no caldria ni fer aquesta revisió, sino només executar el fsck.
 
Els blocs compartits pels inodes estaven a la Cau però, com et deia, no se perquè després van apareixer uns compaartits entre el journal del ext3 i l'inode de la llista de bad-blocks. Cosa que em va deixar molt sorprés.

---

### Post by tacubuntuforums on 2008-05-24
He executat el diagnòstic i no se què fer perquè la prova no ha acabat i no he obtingut resultats.
Això m'ha deixat molt desconcertat perquè he fet tres proves, o sigui, tres vegades la prova llarga i abans d'acabar-la el pc s'ha quedat congelat, tal i com ha estat passant-li sovint els últims mesos. Això fa pensar que tot (fins i tot les penjades) es culpa del disc amb Linux, però no es tant senzill. T'explico:

_Disc hda (Windos):_
hda1: WIndosmil

_Disc hdb (Windos + Linux):_
hdb1: Windosmil (que no faig servir)
hdb2: linux swap
hdb3: / (root de Linux)
hdb4: /home

Els dos discs son Seagte, mateixa velocitat i capacitat.

Evidentment, anteriorment t'he parlat de problemes que ha detectat recentment el programa fsck a la partició hdb4. Per tant he començat per fer la prova al disc hdb.

_Disc hdb_:
Pasada1.- Para bloquejat amb 16 errors trobats, la majoria poc abans de parar (suposo que semblant a lo que va passar a les següents)

Pasada2.-
Troba de 1 a 3 errors, al 61% de la prova, entre els 16 i 17 minuts
Troba de 4 a 12 errors, al 83% de la prova, entre els 24 i 24 min i PARA BLOQUEJAT

Pasada3.-
Troba de 1 a 3 errors, al 61% de la prova, als 15 min
Troba de 4 a 8 errors, al 83% de la prova, entre als 23min i PARA BLOQUEJAT


_Disc hda_:
Una passada.- Termina OK, 0 errors, als 19 minuts


Es clar, no tinc més info de cap dels errors i no tinc ni idea de que passa. Com relacionar tants errors amb el blocs defectuosos? Què fer? Per dos blocs dolents no canviaria el disc, però si estaria molt alerta amb les copies de seguretat; però els 16 errors i les penjades durant les proves que semblen produir-se en un lloc concret?

Ara bé, lo estrany es que les penjades totalment aleatòries (pel meu enteniment) abans d’aquests errors al disc, les ha tingut fent servir Linux en qualsevol moment: durant l'arrancada, durant l'apagada, en moments de poca, molta i nul·la activitat per part de l'usuari, estant esperant a la pantalla de login, etc. A vegades no son penjades i només cauen processos (crec que sempre relacionats amb l'interfaç gràfica; sovint son applets dels panels, surt de la sessió de cop),..però també amb Windos. Amb Windos, des de la mateixa època te fallades dràstiques en qualsevol moment però no es queda penjat sinó que treu la pantalla blava i fa un bolcat de memòria. Dic que es estrany perquè no sé quin disc pot tenir a veure amb les fallades si es que es un disc, i si no, com es que es produeixen tan regularment al fer les proves en hdb?

---

### Post by tacubuntuforums on 2008-05-24
.

---

### Post by papapep on 2008-05-25
Doncs és complicat saber la font real del problema, però has provat a verificar també la RAM que no fos que també estigui tocada? Ho dic per tenir totalment clar que no tens varis problemes sumats que et fan confondre el diagnòstic (M.D. House dixit).
Respecte el no canviar el disc per "uns pocs" sectors, penso (tal i com està la qualitat dels discs d'avui en dia) que si vols estalviar-te molts mal de caps, et surtirà a compte canviar-lo si has confirmat que el ferro té problemes, la veritat, ja que aquests problemes no es solen quedar estancats, sinó que empitjoren i s'agreugen (i no en tinc idea del per què).

---

### Post by tacubuntuforums on 2008-05-29
Sí, també vaig sospitar de la memòria abans de res, al començament del problema, fa molts mesos, i sembla que està bé. Vaig fer moltes passades del memtest86+ i una vegada el vaig deixar unes 6 hores. Tot sumat em sembla que van ser unes 12 hores de repetició del test general i unes poques dels altres especialitzats. Només va trobar errors un test relacionat amb la BIOS però era tan descarat: tot ple d'errors que no li vaig fer cas. Algun amic em va dir que podria ser un error de la BIOS per ser molt vella (5 o 6 anys aprox.) però no ho crec gens perquè les penjades com veus son ben ben aleatòries. També m'han dit que podria ser la font d'alimentació...la veritat es que ja no dono més i estic per portar-lo a revisar.

Jo mes aviat penso que el disc podria haver patit per les penjades i apagades forçades, o sigui, una conseqüència més que la causa. Perquè a més de les cascades amb Windos crec que una vegada es va penjar fent servir un live-cd i no crec que estigues fent servir la swap, ni q tingués montada una partició ....... però vaja, potser ho hauria de tornar a experimentar amb una prova a propòsit i més "científica".

La única pauta que m'ha semblat trobar es que s'em va penjar molt sovint (parlant amb ull estadístic: "massa sovint") quan llegia una llibres online, amb una eina que penso que fa servir un plugin de flash.

Ara tinc un altre problema per fer servir un módem/router però crec que serà millor que ho faci en un altre thread. En aquest cas no es que falli sino que sembla que no es connecta a internet, amb al proveïdor (ISP, que es wanadoo, o ara, orange)  com el que faig servir en aquest moment que només l'endollo a la línia telefònica i ja. Perque em comunico amb ell (l'he configurat amb DHCP...etc.) però no puc sortir de la LAN encara que tingui be la taula d'enrutament i els dns. Inclús m'he connectat amb telnet al router i he fet servir una eina PING pròpia del router però no rebo respostes de fora i sí quan les llenço contra el meu PC.

---

