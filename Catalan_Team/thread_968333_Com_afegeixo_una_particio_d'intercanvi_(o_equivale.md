---
title: "Com afegeixo una particio d'intercanvi (o equivalent)"
date: 2008-11-02
forum: Catalan Team
---

### Post by antoni2 on 2008-11-02
Com es fa per afegir una partició d'intercanvi en Ubuntu, si has 'oblidat' ferla al instal·lar ?

He instalat el Xubuntu 8.10  en un ordinador amb Windows, usant una partició que havia netejat i deixat 'no assignada' en Windows. (necessito el Windows de tant en tant i vull poder fer el double boot. L'instalador de Xubuntu me la reconeix, cap problema. Uso la opcio manual, doncs la automatica insistia a posar el Linux en una altra particio de Windows 'encongida'. 
Ara be, amb la 'reparticio' manual, li dic que usi aquest espai lliure, li dic que la vull com partició primària, i llavors  --- problema: No  em deixa opció (o no se com fer-ho), per fer una  partició d'intercanvi, tot i que m'ho recomana explícitament...

Total, que no la he fet i ara em trobo que potser em cal fer-la.

Preguntes: 
1. Es imprescindible/recomanable ?
2. Com fer-ho sense tenir que reinstal·lar tot ?

Gracies

---

### Post by papapep on 2008-11-02
Benvingut al fòrum, Antoni2.

Et convido a passar-te pels dos fils de capçalera del fòrum, un per presentar-te i l'altre per saber una miqueta com aprofitar de millor manera els recursos que tenim.

> Preguntes:
1. Es imprescindible/recomanable ?

Absolutament imprescindible. Si no en tens, quan, pel que sigui, ocupis tota la RAM el sistema et quedarà penjat.

> 2. Com fer-ho sense tenir que reinstal·lar tot ?


Potser fer-ho amb un live-cd d'Ubuntu mateix. El que et cal és fer servir una eina que es diu GParted (Sistema > Administració > Editor de particions) per fer una mica més petita la partició de l'Ubuntu per deixar espai lliure i crear la de swap (intercanvi).

PD: és absolutament recomanable tenir còpia de totes les dades importants abans de fer el procés de modificació de particions.

---

### Post by CarlesOriol on 2008-11-03
> **papapep said:**
> Absolutament imprescindible. Si no en tens, quan, pel que sigui, ocupis tota la RAM el sistema et quedarà penjat.

No és imprescindible però si recomanable en la majoria dels casos.

Un cas on es bo no usar-la és en un disc dur s'estat sòlid com els que porten els netbooks de baixa capacitat. (cas asus eee)
1r- per que en un ordinador amb 4gb de disc dur ja anem una mica curts
2n- Per que incrementarà el nombre d'accessos al disc dur i per tant en reduirà la vida (que en aquests aparells ja es força limitada)

...

Altres casos poden ser ordinadors vells amb un accés a disc lent on poguem disposar de força memòria. (aquest funcionarà força millor)

Però recorda: sense memòria swap un cop acabada la ram, s'ha acabat. El sistema no et deixarà obrir més programes o fer més operacions fins que en lliuris.

---

### Post by open-pitu on 2008-11-03
Bones! Una bona solució sense que hagis de reinstal·lar tot és redimensionar les particions. Per fer-ho utilitza gparted (molt semblant al PartitionMagic).

per instal·lar gparted:
[INDENT]$sudo apt-get install gparted[/INDENT]
per excutar has de sedr root:
[INDENT]$sudo gparted[/INDENT]

A partir d'aquí redimensiona la partició que vulguis i fes-la d'intercanvi.

Si no va, diga-ho!

---

### Post by antoni2 on 2008-11-03
Gracies a tots ! Sou collon**s

Doncs si, ho he reinstalat tot de nou. Ho he pogut fer perque l'ordinador era nou, i no  hi perdia res, sino el temps que hi passess, que no es tan.

El Gparted funciona molt be. El problema era que no pots tenir més de 4 particions primaries (això ho he apres ara).
El sistema (un Asus Eee PC 1000H amb 160 GB de disc i 1 GB de RAM) em venia amb una instalació una mica particular de Windows, on hi ha ja 3 particions (C:/, D:/ i una altra que diu que es de sistema, molt petita pero que no se sap per a que és). A la partició D:/ original, de 70 GB només hi havia uns 70 MB de dades, aixi que vaig pensar que la podia eliminar i crear dos particionss per Linux, la primaria i una d'intercanvi. Però no ! Al esborrarla el sistema es penja irremisiblement. 
Finalment ho he arreglat reinstalant tot de nou, començant pel Windows (m'ha sorpres no tenir cap problema amb el disc de recuperació que ve de fabrica), i a sobre li he deixat fer tot al instalador del Xubuntu 8.10. Ha instalaat Linux encongint la partició principal del WIndows (C:/ ) fins a 3 GB (mes de 50 GB pel Xubuntu !) i ha creat una altra d'intercanvi. Tot funciona perfecte.

Suposo que lo correcte hauria estat crear una partició 'extended', i fer-hi una de intercanvi a dins, oi?

Al Carles Oriol, sobre la duració dels sistemes amb memoria solid-state, va en serio que duren poc ? Tens alguna referencia ?
Pensava comprar-me un catxibatxe petitet per ferlo anar com a servidor de musica, amb un DAC extern.. he fet proves i el resultat em sembla excelent. Alta fidelitat de debò desde l'ordinador !

Gracies a tothom. Tema resolt.

---

### Post by papapep on 2008-11-03
> Suposo que lo correcte hauria estat crear una partició 'extended', i fer-hi una de intercanvi a dins, oi?

Jo votaria per utilitzar-ne una de primària per la swap, i crear les necessàries per la resta.

> la duració dels sistemes amb memoria solid-state, va en serio que duren poc ?

Bé, més que durar poc és que tenen una vida limitada a nivell de cicles de lectura/escriptura, llarga però limitada. Per això diu que quan menys lectura/escriptura se li faci, de poder-se evitar, millor. :-)

---

### Post by open-pitu on 2008-11-03
Jo tinc el mateix model d' eee-pc que tu. De serie, lamentable venia amb Windows, i el primer que vaig fer va ser provar eee-ubuntu. No em va agradar el tema del ume-desktop i el maximus, i vaig optar per instal·lar xfce de gestor gràfic.

No sé si et pot ser útil però aquí et deixo la meva taula de particions (vaig mantenir la partició de windows i la resta ho vaig adequar)

[IMG]http://open-pitu.webcindario.com/images/Captura.jpg[/IMG]

Amb quina versió vas ara? Has provat eee-ubuntu?

---

### Post by antoni2 on 2008-11-04
ho tinc tot 'verge', es a dir, tal com queda despres de instal·lar de nou el Windows des del disc de recuperacio, i instal·lant el Xubuntu 8.10 a sobree, deixanlt-li fer tot a ell. Un petit problema es que mel posa a la unitat pricipal del Windows un cop encongida -li deixa nomes 5 GB per Windows i sen agafa 75 GB per.

Però ja em va be, perque del Windows he desinstalat tot el que he pogut, reinstallant algunes coses (Skype, Adobe Reader) a la unitat secundaria D: (particio sda2), i posant tot lo nou a aquesta unitat (Firefox, Filemaker gVim, antivirus Avast). He esborrat varios paquetss de Microsoft, i amb tot aixo, em queden lliures 900 MB a la unitat C de Windows, 65 GB a la D, i tira milles. Ara, m'agrada mes el teu, perque crec que tens acces als fitxers del Windows a la particio FAT32, oi?

file:///home/antonio/Desktop/Screenshot.png

---

### Post by open-pitu on 2008-11-05
Des d'Ubuntu puc fer-ho tot tant a la partició FAT32 com a la NTFS.

Per a la ntfs t'has d'instal·lar ntfs-3g que està als repositoris. Per internet hi ha manuals que ho expliquen (possiblement en dos o tres dies en penjaré un a [http://open-pitu.webcindario.com](http://open-pitu.webcindario.com) (és la meva web) on hi haurà com instal·lar el paquet i configurar bé el muntatge.

L'únic que no m'agrada de com ho vaig fer (vaig fer-ho ràpidament perquè em vaig comprar l'eee-pc perquè em va caure el meu antic Acer i necessitava l'ordinador per una entrega i ho vaig fer més provisional que res, ja que vaig provar eee-ubuntu i no sabia que faria) és que és molt gran la partició de Windows pel què l'utilitzo, però en fi, mai se sap.

Si necessites qualsevol cosa ja saps!

---

### Post by antoni2 on 2008-11-05
Gracies, jo també m'ho miraré. No sabia que podies llegir i escriure les particions Windows desde Linux. Si tinc algun problema et faig un truc ;-)

---

### Post by open-pitu on 2008-11-07
Bones! Acabo de penjar com instal·lar ntfs-3g i configurar Ubuntu per a que et monti les particions ntfs amb lectura i escriptura a l'arrencada del sistema.

No copio aquí tot el contingut, et remeto l'enllaç:
[http://open-pitu.webcindario.com/open/index.php?di=76](http://open-pitu.webcindario.com/open/index.php?di=76)

A mi em va funcionar perfecte (a més ho he provat a l'ordinador d'un company i va bé), tot i així si no et va m'ho dius!

---

### Post by CarlesOriol on 2008-11-08
> **antoni2 said:**
> Al Carles Oriol, sobre la duració dels sistemes amb memoria solid-state, va en serio que duren poc ? Tens alguna referencia ?
Pensava comprar-me un catxibatxe petitet per ferlo anar com a servidor de musica, amb un DAC extern.. he fet proves i el resultat em sembla excelent. Alta fidelitat de debò desde l'ordinador !

Hi ha una bona explicació a la mateixa wikipedia: (secció disadvantages) 

[http://en.wikipedia.org/wiki/Solid-state_drive](http://en.wikipedia.org/wiki/Solid-state_drive)

en aquest tipus de sistemes s'intenta que els arxius temporals, logs i com deiem la swap file estigui en la mateixa ram o tinguin escriptura mooooooolt diferida.

---

