---
title: "[SOLVED] Gestió del color amb Unbuntu"
date: 2008-05-19
forum: Catalan Team
---

### Post by carlesdalmases on 2008-05-19
Hola, un parent meu està fent un curs de fotografia digital. A banda dels programes a utilitzar, amb més o menys funcions, al curs li van comentar que l'ubuntu NO gestiona els colors. Sembla que el windows utilitza un sistema anomenat sRGB (tot i que també pot utilitzar un sistema d'Adobe) i que no hi ha cap sistema LINUX que ho faci. He buscat pel Google però no he trobat cap text prou clar :-(

Pel que li van dir, aquesta no gestió del color és crítica alhora de revelar digitalment les fotografies (a partir de fitxers RAW) i, per tant, si es volen uns resultats correctes no es pot fer amb l'Ubuntu.

Algú em pot confirmar si tot això és cert?
I si poso un windows XP amb VirtualBox? El XP virtual gestionarà correctament els colors?

Gràcies.

---

### Post by menut on 2008-05-19
Si és cosa de drivers, no et funcionarà al estar sota l'Ubuntu (ja que és el que "mana"), però si és tema del S.O., et funcionarà.

---

### Post by RainCT on 2008-05-19
Segons tinc entés el problema és que el GIMP treballa principalment amb RGB i no suporta gaire bé els colors CMYK, cosa que fa que a l'imprimir el colors es puguin veure de forma lleument diferent a com es veuen a la pantalla, i a més que en lloc de 16 o 32 bits de profunditat com té el Photoshop només en suporta 8 (tot i que no sé ben bé que vol dir això :P).

Però bé, no em facis massa cas tampoc perquè no en sé gaire, però pel que sé sembla que això només t'ha de preocupar si et vols dedicar al disseny gràfic professionalment (per a productes pensats per a ser impressos: cartells, revistes, etc). En cas que aquest sigui el cas i el GIMP no et serveixi, sempre pots fer servir el Photoshop sota Wine o, millor, com ja dius insta&#320;lar Windows amb VirtualBox.

---

### Post by CarlesOriol on 2008-05-19
Si, tens raó. Però tingues en compte que els colors exactes sols els pots aconseguir en sistemes molt molt concrets i molt professionals i cars.

D'altra banda malgrat que el sRGB intenta ajustar els colors entre dispositius fa el que bonament pot i no és cap garantia de res.

Rain: No té res a veure amb la codificació del punt és la modificació d'aquest color sobre un dispositiu per tal que un mateix RGB CMYB HSI o PANTONE o com vulguis definir el color es mostri tant similar com sigui possible en diversos dispositius.

CarlesDalmases: En la majoria de casos no t'ha de preocupar. Cal que facis res molt crític on t'afecti profundament?

---

### Post by bratac on 2008-05-19
Carles, per a que ubuntu gestioni el color has d'instal·lar els paquet icc-profiles des del **synaptic**. Un cop fet això has de dir a cada programa, scribus, inkscape i gimp que gestioni el color a partir dels perfils que has instal·lat. Per a fer-ho hauràs de cercar l'opció pertinent a les preferències de cada programa. Si et fa cercar els perfils icc, normalment els instal·la a la carpeta /usr/share/color/icc.
 
Si l'únic perfil que l'interessa és el sRGB no tindras cap problema. Si vols treballar amb quatricromia (CMYK, COATED...) ho tindrà més complicat, sobretot si ho vols fer amb gimp. Amb scribus i inkscape és més senzill, tot i que al ser una característica nova de l'inkscape no n'he fet proves.

fins aviat, 

Alfred

---

### Post by oriolsbd on 2008-05-19
Hola, Carles.

Hi ha una opció, però no sé si és la que busques. Entenc que el que vols és configurar els colors de pantalla per tal que s'acabi imprimint exactament el mateix color que veus per pantalla.

Si tens instal·lat l'EnvyNG, a "Sistema\Administració" hi tens l'opció "NVIDIA X Server Settings". Si la teva targeta és ATI, hi tindràs l'opció "ATI X Server Settings" on suposo que podràs fer alguna cosa semblant a la que et comento.

Bé, un cop obert l'NVIDIA X Server Settings, hi tens diverses opcions. A "X Server Display Configuration", hi tens una pestanya que es diu "X Screen". A "Color Depth", posa-hi el màxim valor. Em sembla que per defecte ja hi ha 24 bits, que és el màxim.

Ara, a l'apartat "X Screen 0" (si tens més d'un monitor hauràs de configurar cada "X Screen 1", "X Screen 2", etc.) hi ha l'apartat "X Server Color Correction", i em sembla que és aquesta l'opció que estàs buscant. Com a mínim, es pot modificar la forma de visualitzar tots els colors en conjunt o els vermells, els verds i els blaus per separat.

Per cert, si no recordo malament (però no n'estic segur del tot), la diferència entre els 24 bits i els 32 bits és que a 24 bits tens 8 bits per a cada color, i a 32 bits tens els 24 bits dels colors més 8 bits de nivell de transparència.

Salutacions,

Oriol.

---

### Post by CarlesOriol on 2008-05-20
> **bratac said:**
> Carles, per a que ubuntu gestioni el color has d'instal·lar els paquet icc-profiles des del **synaptic**.... 

Això soluciona el gairebé tots els problemes que comentaven. 

Bratac, No ho sabia gràcies.

---

### Post by carlesdalmases on 2008-05-22
Doncs si, sembla que instal·lant el paquet icc-profiles es solucionen tots els problemes. Ho provaré.
Moltes gràcies a tots

---

