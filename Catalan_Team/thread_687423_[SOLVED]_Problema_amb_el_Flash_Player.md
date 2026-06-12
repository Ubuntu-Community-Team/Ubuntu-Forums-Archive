---
title: "[SOLVED] Problema amb el Flash Player"
date: 2008-02-04
forum: Catalan Team
---

### Post by eduardsola on 2008-02-04
Aviam gent, porto dies, fins i tot setmanes intentant configurar el PC perquè pugui veure els vídeos de YouTUbe i altres webs que fan servir el Flash Player bé. Ho he provat tot, m'he baixat la versió 9, he instal·lat el que hi ha als repositoris "flashplugin-nonfree". Els vídeos els veig, però la barra del reproductor està tallada per la meitat, a més a més, quan obro la pàgina del video que vull reproduir, el PC carrega molt la RAM.

He provat amb el GNASH, però res.

Què teniu vosaltres per veure el Youtube?

Gràcies per avançat

---

### Post by jodufi on 2008-02-04
Jo amb el "flashplugin-nonfree" em funciona sense problemes. Utilitzes l'Ubuntu de 64 bits?

També podries provar el swfdec, que aquest és lliure i diuen que funciona perfectament amb vídeos del youtube.

Pel tema de la RAM, no et refereixes a la CPU? Perquè a mi si que em carrega molt la CPU.

---

### Post by eduardsola on 2008-02-04
Utilitzo la de 32 bits, i perdona, sí, és la CPU (lapsus).

He desinstal·lat el flash player normal i el gnash i ara hi tinc el swfdec-mozilla i el flashplugin-nonfree, quan entro a la pàgina de youtube em diu que he de baixar un connector... i quan obro la pestanya em diu que he de baixar-me el gnash swf player i el flash player altre cop :S

---

### Post by papapep on 2008-02-04
Símplement anant a la pàgina d'Adobe on trobes tar.gz amb la versió 9 i instal·lant-lo t'ha de funcionar perfectament. Tota la resta eliminala que només et portarà problemes.

[http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu](http://www.howtoforge.com/native_linux_flash_player9_in_ubuntu)

---

### Post by eduardsola on 2008-02-04
Vaig a provar-ho...

He fet el que deia a la web, fins que he arribat a aquest pas:

You will be asked a few questions:

Copyright(C) 2002-2006 Adobe Macromedia Software LLC. All rights reserved.

Adobe Flash Player 9 for Linux

Adobe Flash Player 9 will be installed on this machine.

You are running the Adobe Flash Player installer as the "root" user.
Adobe Flash Player 9 will be installed system-wide.

Support is available at [http://www.adobe.com/support/flashplayer/](http://www.adobe.com/support/flashplayer/)

To install Adobe Flash Player 9 now, press ENTER.

To cancel the installation at any time, press Control-C. <-- <ENTER>

NOTE: Please exit any browsers you may have running.

Press ENTER to continue... <-- <ENTER>

[B]Please enter the installation path of the Mozilla, SeaMonkey,
or Firefox browser (i.e., /usr/lib/mozilla): <-- /usr/lib/mozilla[/B]

Aquí, quan poso el que hi diu: /usr/lib/mozilla, em posa això:
```

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.
```

I no em deixa fer res més...

---

### Post by papapep on 2008-02-04
Doncs o se t'escapa alguna cosa o alguna part del ferro no et va bé.

---

### Post by CarlesOriol on 2008-02-04
Hi ha dies que l'insta&#320;lador de flash no funciona bé degut a que al ser programari restrictiu no es pot incorporar directament als repositoris i el paquet realitza la insta&#320;lació des d'una font externa.

Ara mateix va bé. Fins i tot la insta&#320;lació de 64 bits. Si pots torna-ho a provar. I evidentment si fos el cas de la insta&#320;lació de 64 bits realitza un munt de feines que usant l'insta&#320;lador original com t'indica en mestre pep no t'aniria. (en 32 si... eh... )

Esperem que amb el temps poguem gaudir d'un gnash de qualitat per evitar-nos aquests mals de cap.

---

### Post by Daerun on 2008-02-04
A mi em va passar el mateix quan vaig arribar en aquest punt. Intenta el següent: quan hi arribis, escriu:

** /usr/lib/firefox**  i   ENTER

Jo tinc el Gutsy i aquesta es la carpeta on està el Firefox.

---

### Post by eduardsola on 2008-02-04
Ja estàààà!

Gràcies a tots per l'ajuda, ja puc veure els vídeos tranquil·lament.

Salut!

---

### Post by Daerun on 2008-02-05
Em creureu si us dic que vaig trigar dos dies en poder-me'l instal·lar per culpa d'aquesta collonada (amb perdó), abans de descubrir que el problema era que la ruta especificada per defecte era errónea? :lol:

---

### Post by eduardsola on 2008-02-05
> **Daerun said:**
> Em creureu si us dic que vaig trigar dos dies en poder-me'l instal·lar per culpa d'aquesta collonada (amb perdó), abans de descubrir que el problema era que la ruta especificada per defecte era errónea? :lol:

Jo he mirat l'arbre de directoris, i en veure que la carpeta existeix, la del mozilla, he pensat que no era aquest el problema... una mica liat tot, la veritat!

---

### Post by Daerun on 2008-02-05
Això mateix és el que em va desconcertar a mi. El problema és que el FIrefox no estroba en aquesta carpeta, si no a la Firefox.
No entenc perquè existeix la carpeta Mozilla aleshores:confused:

---

### Post by eselma on 2008-02-06
En versions anteriors, recordo que hi havia el directori "*/usr/lib/mozilla-firefox*" i el "*/usr/lib/mozilla-thunderbird*", a més del directori genèric "*/usr/lib/mozilla*". Els *plugins* presents a aquest darrer tenien efecte sobre els primers. 

Darrerament, sembla que tant el *firefox* com el *thunderbird* tenen personalitat diferenciada del projecte *mozilla*, i això es reflecteix en directoris (també al directori personal a "*/home/usuari*") i als mateixos noms del fitxer executable a "*/usr/bin/*". El problema apareix en casos com el que esmenteu, ajudat pel fet que diverses distribucions potser encara usen l'esquema anterior.

Quan estem acostumats al mètode nou, ens el tornaran a canviar...

---

### Post by Daerun on 2008-02-06
Doncs això és una errada per part de mozilla. És a dir, no una errada, si no que no és gens seriós crear un explorador per un programari lliure i no fer-lo ben estandaritzat en totes les seves versions perquè sigui el máxim de compatible possible...

---

