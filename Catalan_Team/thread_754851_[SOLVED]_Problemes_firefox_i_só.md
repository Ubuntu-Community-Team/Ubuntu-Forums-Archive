---
title: "[SOLVED] Problemes firefox i só"
date: 2008-04-14
forum: Catalan Team
---

### Post by auska1714 on 2008-04-14
Hola,

Utilitzo l'ubuntu 7.10 des de fa una setmana aproximadament i he pogut arreglar la majoria de problemes. 

Tot i això necessitaria que m'expliquesiu que he de fer per arreglar el firefox ja que no sé perquè però quan vull veure un video del youtube que han penjat a una altre web (no el link, sino el video en si), no es veiu. I un cop en el youtube les icones em queden sobreposades tot hi que em deixa veure el video. A més hi han webs com es aquest cas; [www.koxx-one.com](www.koxx-one.com) que hauria de començar amb un flash i en lloc d'això em surt un requadre petit de color verd amb l'interió negre a la part superior esquerra de la pantalla. Ve tot del mateix problema? Com o puc arreglar?

Un altre problema es que no se com configurar els altaveus de l'equip de musica a l'ordinador per tal de que sonin simultàniament als de l'ordinador.

Gràcies per avançat,

Salut!

---

### Post by SiscoGarcia on 2008-04-14
Hola auska1714, benvingut/da al fòrum ubuntaire (per cert, passat pel [fil de benvinguda]("http://ubuntuforums.org/showthread.php?t=562776") i explica'ns de tu).

Una altra cosa que pots fer és no barrejar coses, **cada problema un fil**, així permets que la gent pugui resoldre't millor els problemes i, el que potser és més important, que una altra persona que tingui un d'aquests problemes pugui trobar abans la solució. En aquest sentit aniria bé que et miressis el[ fil d'introducció]("http://ubuntuforums.org/showthread.php?t=599965") a l'ubuntu.

Després d'haver emulat els mestres, intentaré ajudar-te amb el tema del firefox, ja has instal·lat el connector pel flash? Connecta't a l'adreça "about:plugins" sense cometes a veure si el tens instal·lat i ja diràs.

Benvingut/da!

---

### Post by SiscoGarcia on 2008-04-14
EDITO: Com que abans els dos punts seguits de la p m'han donat una emoticona, adjunto la captura del meu firefox amb l'adreça que et proposava.

Ja diràs.

---

### Post by auska1714 on 2008-04-14
Per tal de que veieu millor el problema us deixo la captura de pantalla dels dos casos en els que us he parlat:

[http://tinypic.com/view.php?pic=160r0ig&s=3[]("http://tinypic.com/view.php?pic=160r0ig&s=3[")

fixeu-vos en la barra de sota el video:

[http://s3.tinypic.com/2qv6uj8.jpg]("http://s3.tinypic.com/2qv6uj8.jpg")

amb el tema del conector em surt això:

[http://s3.tinypic.com/2h5l1fk.jpg]("http://s3.tinypic.com/2h5l1fk.jpg")

---

### Post by SiscoGarcia on 2008-04-14
Anem a pams:

> Per tal de que veieu millor el problema us deixo la captura de pantalla dels dos casos en els que us he parlat:

[http://tinypic.com/view.php?pic=160r0ig&s=3](http://tinypic.com/view.php?pic=160r0ig&s=3)

Aquest enllaç porta a un lloc "estrany", jo el revisaria o el treuria :-k


> amb el tema del conector em surt això:

[http://s3.tinypic.com/2h5l1fk.jpg](http://s3.tinypic.com/2h5l1fk.jpg)

Aquest tema diria que està resolt, més encara quan dius que pots veure el vídeo, com sembla per la captura que ens has passat.

> 
fixeu-vos en la barra de sota el video:

[http://s3.tinypic.com/2qv6uj8.jpg](http://s3.tinypic.com/2qv6uj8.jpg)

Aquest tema de la superposició de barres no el controlo, potser tingui a veure la resolució de pantalla?

Finalment, per adjuntar-nos una captura, pots fer-ho baixant per sota de la caixa de text (on escrius el missatge), allà veuràs escrit en roig "Additional Options" (sense cometes), si baixes una mica més, trobaràs una opció que és "Attach Files", allà piques "Manage Attachments" i cerques allò que vulguis adjuntar, ho puges i ja està. 

Fàcil oi?

Salut!

---

### Post by papapep on 2008-04-14
Tens activat el compiz? De ser així, prova a desactivar-lo, a veure si et funciona millor.

Quina gràfica i amb quin controlador tens?

---

### Post by pespin on 2008-04-14
Xavals! sembla ser segons el about:plugins que té la versió 8 del flash i no la 9, deu ser aquest el problema!

Quina versió d'ubuntu utilitzes?

EDIT: Ara que m'hi fixo, diria que més aviat està utilitzant el Gnash, d'aqui venen els problemes hehe (la versio 8... deu ser per la compatibilitat que diu que té el Gnash)

---

### Post by auska1714 on 2008-04-14
Ja ho he pogut arreglar, a set posar això a la terminal i s'ha arreglat;

sudo aptitude remove mozilla-plugin-gnash
sudo aptitude reinstall flashplugin-nonfree

Merci  ;)

Salut!

---

### Post by SiscoGarcia on 2008-04-14
Doncs ara caldria que marquessis el fil com a resolt:" Thread Tools>Mark This Thread As Solved"

---

### Post by lluisanunez on 2008-04-15
Doncs ara només et falta el corrector de català per al Firefox :-P

---

