---
title: "[SOLVED] Clauer IdCAT i Ubuntu 8.04"
date: 2008-10-12
forum: Catalan Team
---

### Post by LinuxDOG on 2008-10-12
Hola a tothom.

Estic intentant instal·lar el soft del clauer de l'IdCAT, en concret el ClauerLinux-3.0 i no me'n surto.

Estic seguint la guia que es troba a:

[http://www.libertium.net/index.php?option=com_content&task=view&id=20&Itemid=5]("http://www.libertium.net/index.php?option=com_content&task=view&id=20&Itemid=5")

tot i que diu que es per Ubuntu 7.10, pero a l'hora d'engegar el dimoni "clos" amb

/etc/init.d/clos start 

m'apareix el missatge:

*/usr/local/sbin/clos: error while loading shared libraries: libCRYPTOWrap.so.0: cannot open shared object file: No such file or directory*

tal i com diu la guia.

El meu problema apareix quan, també seguint els consells de la guia, intento instal·lar els paquets libcrypto++6 i libcrypto++-dev, que es quan em trobo que el libcrypto++6 ha estat substituit pel libcrypto++7 (utilitzant Sinaptic i apt).

Pensant que possiblement pugui funcionar amb l aversió 7, la instal·lo, però segueix sense funcionar, i tornant el mateix missatge de:

*/usr/local/sbin/clos: error while loading shared libraries: libCRYPTOWrap.so.0: cannot open shared object file: No such file or directory*

Algú ha conseguit instal·lar el clauer? Com s'ho ha fet?

Qualsevol ideia serà benvinguda. Gràcies d'avançada.

---

### Post by jaumell on 2008-10-12
Doncs jo el tinc instal·lat i funcionant amb el 8.04, sense problemes.

Instruccions a [http://clauer.nisu.org/linux](http://clauer.nisu.org/linux)

En tot cas, revisant les meves notes, em surt que vaig instal·lar:

g++
libstdc++6-4.2-dev
libnss3-dev
libssl-dev
gawk

Sort!

---

### Post by LinuxDOG on 2008-10-13
Gràcies per la resposta, però no m'ha funcionat.

He baixat el nou paquet (jo feia servir el 3.0.0) i he instal·lat els que em comentes, però segueix apareixent el mateix error en engegar el clos:

*/usr/local/sbin/clos: error while loading shared libraries: libCRYPTOWrap.so.0: cannot open shared object file: No such file or directory*

---

### Post by _DarkEagle_ on 2008-10-13
Bé, l'altre dia mateix estava instal·lant el Clauer en la meva ubuntu i vaig fer un petit tutorial, espero que et serveixi, l'error que et surt està explicat en el tutorial:

Aquí us deixo la direcció: [http://blog.nucl3ar.net/2008/10/09/idcat-clauer-en-ubuntu-hardy-con-firefox-3/](http://blog.nucl3ar.net/2008/10/09/idcat-clauer-en-ubuntu-hardy-con-firefox-3/)

Salut !

---

### Post by Tomàs M. on 2008-10-13
Doncs aquí teniu el meu :lolflag: [http://www.tomi.cat/2008/10/i-avui-idcat.html](http://www.tomi.cat/2008/10/i-avui-idcat.html)

---

### Post by LinuxDOG on 2008-10-13
He seguit els consells de _DarkEagle_ i he aconseguit instal·lar el programa (es tractava d'un tema de paths).

També he comprovar el problema amb el firefox, però he instal·lat el firefox-2 i ja he pogut executar el .sh. No obstant, depsres que em funciones des de firefox, he desinstal·lat el firefox-2 i segueix funcionant correctament.

Moltes gràcies a tots per la vostra ajuda.

---

### Post by _DarkEagle_ on 2008-10-13
Si, jo també vaig desinstalar el Firefox 2 posteriorment ... i sense cap problema jejeje

M'alegro que t'hagui funcionat bé !!

Salut !

---

### Post by QrK0 on 2008-11-24
A més de les llibreries que comenta en Jaumell, he hagut d'insta·lar les opensc i libopensc.
Fins que no he instal·lat això no hi ha hagut manera d'engegar el servei Clos.

Intrepid Ibex i Clauer 3.0

Salut!

---

### Post by ernestux on 2010-02-18
Hola,

En fer al final de tot el procés:  firefox-install-pkcs11.sh  s'obre una finestra: file///tmp/install.html,però no fa res més. A la consola diu "instalació finalitzada", i no s'obre cap diàleg per carregar cap mòdul.
He intentat fer apt-get install firefox-2 però no és disponible per karmic.
Alguna idea?
Gràcies

---

### Post by SiscoGarcia on 2010-02-18
> **ernestux said:**
> Alguna idea?

Has provat de fer una cerca més actualitzada, pensa que el fil és sobre l'ubuntu 8.04? [Aquí]("http://blog.nucl3ar.net/2008/10/09/idcat-clauer-en-ubuntu-hardy-con-firefox-3/") pots trobar alguna cosa sobre firefox3, [aquí]("http://trasier.blogspot.com/2010/01/clauer-idcat.html") referent a ubuntu 9.10; si no potser hi és a [http://tinyurl.com/ykrqvyr](http://tinyurl.com/ykrqvyr)

No ho sé perquè no faig servir aquest clauer, però ja tens feina per remenar ;)

---

### Post by Tomàs M. on 2010-02-23
No recordo exactament què vaig fer, però tinc guardat aquest enllaç des del novembre; espero que et serveixi: [http://www.imatgedart.com/wiki/tutorials:gnulinux:certificats_dig:idcat](http://www.imatgedart.com/wiki/tutorials:gnulinux:certificats_dig:idcat)

Salut!

---

