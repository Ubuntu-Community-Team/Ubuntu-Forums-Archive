---
title: "Suposat problema connector Java  Firefox"
date: 2007-12-17
forum: Catalan Team
---

### Post by Joan Marc on 2007-12-17
Hola
En algunes pàgines web (p.e. [www.youtube.com](www.youtube.com) o [www.planetderbi.com](www.planetderbi.com)), tinc alguns problemes amb els gràfics.
Més concretament, al YouTube, no es carrega correctament el reproductor, i no puc fer servir l'opció de pantalla completa o la d'avançar, a la pàgina del planetderbi, no puc clicar l'opció de l'esquerra (que serveix per anar, per exemple al fòrum de la web).
Jo crec que és un problema Java, però estic bastant convençut que ho tinc ben instal·lat...
Teniu alguna sol·lució?

Gràcies ;)

PD: Perdó pel títol...és "Suposat problema Java"

---

### Post by jodufi on 2007-12-17
Més que un problema del java, no pot ser un problema del flash?
Intenta instal·lar el paquet "ubuntu restricted extras" a veure si així et funciona.

---

### Post by Joan Marc on 2007-12-17
Em diu que "Can't be authenticated"... és segur instal·lar aquest paquet?

Gràcies

---

### Post by papapep on 2007-12-17
Aquest paquet instal·la un munt de coses:

[http://packages.ubuntu.com/gutsy/metapackages/ubuntu-restricted-extras](http://packages.ubuntu.com/gutsy/metapackages/ubuntu-restricted-extras)

Respecte si és "segur", si et refereixes a la seguretat de que si és fiable, doncs tots els paquets dels repositoris d'Ubuntu són de fiar.  Si alguna vegada un paquet ha provocat errors de pes, al cap de poc ha estat solventat i es pot arreglar.

---

### Post by Joan Marc on 2007-12-17
Gràcies, però els problemes no s'han sol·lucionat... a cas he de reiniciar l'ordinador perquè tinguin efecte?

A part d'això, si tots els paquets són de fiar, com és que surt el misatge d'advertència?

Gràcies :)

---

### Post by papapep on 2007-12-17
No sé com funciona aquest joc, però segur que no parla del paquet .deb, sinó del funcionament del joc que deu accedir a algun contingut o servidor per internet. I si, pel que costa reinicia l'ordinador, a veure si així et funciona.

---

### Post by Joan Marc on 2007-12-17
Bé, no era un joc, sinó que era el paquet de "ubuntu restrincted extras" des del Synaptic...

Lo de les pàgines web continua sense funcionar, fins i tot després de reiniciar.

Gràcies.

---

### Post by papapep on 2007-12-17
Ups, he barrejat fils...massa pressa.

Jo provaria a tornar a instal·lar el connector de flash:

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)

No tindràs el connector de Macromedia i el Gnash instal·lats simultàniament, oi?

---

### Post by Joan Marc on 2007-12-18
Ostres... em sembla que si... vaig instal·lar els dos des del web del [www.youtube.com](www.youtube.com)...

Per cert, com s'instal·la un tar.gz?

Gràcies :)

---

### Post by papapep on 2007-12-18
Obre un altre fil per això, sinó es converteix en un guirigall.

Doncs jo desinstal·laria el gnash i reinstal·laria el Flash.

---

### Post by Joan Marc on 2007-12-18
Dacord, ja obriré el nou post quan hagem resolt això :)

Pel que fa al tema del post, he dsinstal·lat per complet el gnash, i he reiniciat l'ordinador, però ara encara és pitjor, m'explico, cuan vull veure un video al Youtube em surt el missatge (adjunt <1>), i a la part superior una opció (adjunt <1>), però si la segueixo, i li donc a instal·lar el Flash, em diu que ja està instal·lat (adjunt <2>)... però continua sense funcionar.

Bé, suposo que m'he explicat be...

Gràcies.

---

### Post by papapep on 2007-12-18
És igual el que et digui, ves a l'enllaç de macromedia que t'he passat a un post anterior i instal·lal de nou. Fa poc a una altra persona li va passar un cas clavat.

---

### Post by Joan Marc on 2007-12-18
Bé... m'he espavilat per apendre a instal·lar el tar...
Però em surt l'error següent des del terminal:
```
gami@Gami:~$ sudo /home/gami/Escriptori/install_flash_player_9_linux/flashplayer-installer
[sudo] password for gami:

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

```

Gràcies

---

### Post by Joan Marc on 2007-12-24
Algú em pot dir alguna solució?

Gràcies.

---

### Post by Josep Maria on 2007-12-26
Hola Joan Marc.
Jo vaig tenir el mateix problema i ho vaig arreglar de la seguent manera: Dins de Firefox obre el menu Eines -complements.
Desactiva l'extensió Ubufox.
Reinicia el navegador, i obre una web que tingui una aplicació Flash, el You tube o Vilaweb per exemple.
Et demena d'instal.lar el connector, et surt una pagina d'acceptació dius Ok, s'instal.la i llestos.
Si les extensions de firefox les gestiona Ubuntu, no hi ha manera d'instal.lar el Flash player.
Per cert amb l'altre visualitzador, el Gnash, al menys des del meu Ubuntu, no puc veure cap video del You Tube.

Josep Maria

---

### Post by Joan Marc on 2007-12-26
Hola Josep Maria,
Primer de tot moltes gràcies per respondre'm.
He fet el que m'has dit, però acabo al mateix lloc, des del terminal em surt el mateix:

```
gami@Gami:~$ sudo /home/gami/Escriptori/install_flash_player_9_linux/flashplayer-installer
[sudo] password for gami:

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.
```

A tu també et sortia aquest missatge Josep Maria?

Bé, moltes gràcies!

Salut!

---

### Post by papapep on 2007-12-26
El problema que tens és que intentes instal·lar programari de 32 bits en una màquina que té un processador (i pel que sembla la versió de Ubuntu que has instal·lat) de 64 bits.

Aleshores, hauries de seguir les instruccions que descriuen aquí:

[http://ubuntuforums.org/showthread.php?t=476924&highlight=flash](http://ubuntuforums.org/showthread.php?t=476924&highlight=flash)

---

### Post by Joan Marc on 2007-12-26
Moltes gràcies papapep!
Per fi! Ara ja va bé!
Tinc una pregunta, però potser és per un altre post:
> **papapep said:**
> El problema que tens és que intentes instal·lar programari de 32 bits en una màquina que té un processador (i pel que sembla la versió de Ubuntu que has instal·lat) de 64 bits.

Què he de fer sempre no pugui instal·lar programari de 32 bits a la meva màquina de 64 bits? (No sé si recordes que ja vaig proposar un post anteriorment <Error en instal·lar paquet i386>, és el mateix?)

Ostres... esperu que no siguin massa preguntes juntes :S

Com sempre, moltes gràcies :)

---

### Post by patrickfromspain on 2007-12-27
O be forces el paquet a insta&#320;lar-se o en busques una versió de 64bits. Tens del problema de que amb 64bits hi ha varies aplicacions que no funcionen de manera nativa: el flash player,el connector de sun pel firefox i alguna més, com alguns videos en format WMV.

Jo tinc un processador de 64bits i faig servir la versió de 32bits de l'ubuntu... ja que l'altra no hem compensava per a res els maldecaps que hem donava.

Salut!

---

### Post by Joan Marc on 2007-12-27
Patrick, a quins maldecaps et refereixes?

Saluts

---

### Post by Joan Marc on 2007-12-27
Ola a tothom,
Males noves... quan intento visualitzar una web que fa servir flash (youtube, fotolog...) el Mozilla Firefox es queda penjat, i no puc fer res més que pulsar desesperadament la creu de tancar fins que se'm tanca..
Avans que això passés, m'havia sortit una advertencia de l'ubuntu que em deia que no podia afegir ni treure cap programa de l'ordinador, i que la solució era que fes al terminal: sudo apt-get install -f.
Si torno a fer el mateix al terminal em surt el següent:
```

gami@Gami:~$ sudo apt-get install -f
[sudo] password for gami:
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
The following packages were automatically installed and are no longer required:
  nspluginwrapper libbtctl4 libboost-date-time1.34.1 qt3-assistant
  libboost-thread1.34.1 libopenobex1 qt3-doc openclipart-png libgnomebt0
Use 'apt-get autoremove' to remove them.
0 actualitzats, 0 nous a instal·lar, 0 a eliminar i 0 no actualitzats.
gami@Gami:~$ 

```

Hi té res a veure?
Teniu alguna sol·lució?

Gràcies!

---

### Post by papapep on 2007-12-27
Executa el firefox des d'un terminal, a veure quins missatges mostra.

---

### Post by Joan Marc on 2007-12-27
Vols dir sudo firefox?

---

### Post by pespin on 2007-12-27
El sudo no cal:

```
firefox
```

D'aquesta manera quan es penji potser deixa a la terminal alguna inforamció sobre l'error :)

---

### Post by Joan Marc on 2007-12-27
L'he executat des del terminal i el firefox s'obre amb normalitat, al terminal no apareix cap mena de missatge.

Gràcies

---

### Post by jodufi on 2007-12-28
Quan l'executis des del terminal, ves a la pàgina on es penja (youtube i companyia), a veure si deixa rastre

---

### Post by Joan Marc on 2007-12-28
Al posar la pàina web no em surt res, només, al forçar la sortida posa killed...(un pel salvatge no?)

Gràcies!

---

### Post by papapep on 2007-12-28
Quan en un dels posts anteriors dius:

> Per fi! Ara ja va bé!

Què havies fet per a que, inicialment, et funcionés?? Què havies instal·lat o desinstal·lat, configurat o el que fos? (explica-ho amb detall, si us plau) Quan vas dir que funcionava, què et va motivar a dir-ho? Podies veure videos del Youtube? Has fet alguna cosa després que pogués provocar que tornés a deixar de funcionar?

---

### Post by Joan Marc on 2007-12-29
Vaig seguir el fil que em vas posar:
[http://ubuntuforums.org/showthread.php?t=476924&highlight=flash](http://ubuntuforums.org/showthread.php?t=476924&highlight=flash)

Sí que podia veure els videos, també podia fer servir la barra de sota dels videos, amb les opcions de parar, començar...

Sí que vaig fer alguna altre cosa després:
> Avans que això passés, m'havia sortit una advertencia de l'ubuntu que em deia que no podia afegir ni treure cap programa de l'ordinador, i que la solució era que fes al terminal: sudo apt-get install -f.
Si torno a fer el mateix al terminal em surt el següent:

Code:
gami@Gami:~$ sudo apt-get install -f
[sudo] password for gami:
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
The following packages were automatically installed and are no longer required:
  nspluginwrapper libbtctl4 libboost-date-time1.34.1 qt3-assistant
  libboost-thread1.34.1 libopenobex1 qt3-doc openclipart-png libgnomebt0
Use 'apt-get autoremove' to remove them.
0 actualitzats, 0 nous a instal·lar, 0 a eliminar i 0 no actualitzats.
gami@Gami:~$

Gràcies!

---

