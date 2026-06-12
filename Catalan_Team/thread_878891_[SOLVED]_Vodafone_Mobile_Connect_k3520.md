---
title: "[SOLVED] Vodafone Mobile Connect k3520"
date: 2008-08-03
forum: Catalan Team
---

### Post by sakuraya on 2008-08-03
Hola a tots. No fa massa temps que tinc instal.lat el ubuntu 8.04, i no tinc gaires coneixements d'informàtica. M'he comprat aquest aparell per poder-me connectar, però només em funciona amb les "finestres". He intentat fer de tot, però no me n'ensurto. He consultat al google durant tota una setmana, he consultat un munt de pàgines, de forums, a la web de Vodafone,... No hi ha manera. No trobo gens d'informació sobre aquest model. He trobat uns enllaços a [www.betavine.net](www.betavine.net), m'he descarregat dos arxius, però al instal·lar-los amb synaptic em surt un error, que només ha trobat un dels 21 arxius, i em diu que em connecti per baixar-los, i aquí està el problema.
Algú sap com ho podria fer per a poder-me connectar amb aquest aparell?
Moltíssimes gràcies. En quant solucioni això, abandono les finestres. Gràcies.

---

### Post by papapep on 2008-08-03
Quins fitxers has baixat en concret? a Betavine n'hi ha un munt...

---

### Post by sakuraya on 2008-08-04
Moltes gràcies papapep. 
Són vodafone-mobile-connect-card-driver-for-linux-2.0.beta2.ubuntu-installer.run
vodafone-mobile-connect-card-driver-for-linux-2.0.beta3.tar.gz
vodafone-mobile-connect-card-driver-for-linux-2.0.beta3-ALL-i386-installer.run
vodafone-mobile-connect-card-driver-for-linux-1.99.17_i386.deb

El sistema que tinc es un portàtil intel 32bit.

---

### Post by papapep on 2008-08-04
Abans que res, no tens CAP manera de connectar-te a una xarxa per cable per a instal·lar-ho? t'estalviaria molts mals de caps i temps...

No hi ha cap ànima caritativa que et deixés 15 minuts de connexió???....

Afegint el repositori del que parlen a Betavine seria un pis-pas.

---

### Post by papapep on 2008-08-04
Bé, ara ho poso al fil correcte X-)

Si no tens possibilitat de connectar via ethernet, haurem de fer això:

Ja que tens el .deb descarregat, mirarem quines dependències té a veure si ens en sortim amb poquets paquets ;-)

Segons l'aptitude, les dependències són:

 - hal
 - python-vmc
 - wvdial



Primer cal saber si els tens instal·lats. Ho pots saber fent a un terminal "sudo aptitude search hal python-vmc wvdial". Els que la línia comenci per "i" vol dir que sí estan instal·lats.

Els que no estiguin instal·lats, els descarregues com has fet abans amb els paquets del vodafone-mobile-connect.

Un cop ho hagis fet, i els tinguis accessibles a l'Ubuntu, cal fer a un terminal:

```
sudo dpkg -i python-vmc
```

per exemple, i instal·lar els paquets en l'ordre que les dependències no es queixin. 
Ja diràs com et va.

---

### Post by sakuraya on 2008-08-06
Hola de nou.

Per fí he aconseguit instal-lar aquests arxius, que no els tenia. Ara ja surten amb "i". Però quan faig 
sudo dpkg -i python-vmc o les altres dues, em surt el missatge "dpkg: s'ha produït un error en processar phyton-vmc (--install): no es pot accedir a l'arxiu: No such file or directory.

Després d'haver baixar arxius de tot tipus, no sé si té relació amb això, però ara ja em surt el programa de Vodafone al menú Internet, tot i que no funciona en absolut. I també he detectat que al Synaptic em surt un arxiu, el vodafone-mobile-connect-car-driver-for-linux, com a "trencat". Després, si intento insta.lar l'arxiu .deb o qualsevol dels que anaven junts, m'indica "les dependencies estan trencades". Suposo que tot deu tenir relació.
Moltes gràcies.

---

### Post by patrickfromspain on 2008-08-06
l'error que et dona es que no trova els arxius. Estas fent el dpkg -i des d'un directory diferent d'on tens els arxius.

---

### Post by sakuraya on 2008-08-29
Hola a tothom. Moltes gràcies a tots. Per fi ho he aconseguit. Us estic escrivint des de l'Ubuntu. El meu amic Josep Maria m'ha ajudat, i ho hem fet un pèl a la valenta: hem formatat l'ordinador, i hem instal.lat una altra vegada Ubuntu des del CD. De seguida ha reconegut la connexió ADSL que teníem connectada, i hem començat a instal.lar el programa que dèiem. Quan ha començat, de seguida demanava baixar els altres 21 arxius, i un cop fet, de seguida a funcionat. No ha calgut fer cap adaptació, hem seleccionat que busqui la configuració automàticament i tot ha anat perfecte. Encara riu quan m'ha vist la cara que he posat quan he vist que s'havia connectat.
Gràcies a aquesta ànima caritativa m'he pogut alliberar de les finestres. De fet, funciona molt més ràpid tant a l'hora de connectar-se com de navegar. 
:guitar:Moltes gràcies.:guitar:

---

### Post by papapep on 2008-08-29
Perfecte. Enhorabona per haver-te'n sortit ;-)

Ara [marca el fil com a resolt]("http://ubuntuforums.org/showthread.php?p=3687595#post3687595"), si us plau.

> 12.- Acabeu amb una nota sobre la solució

Com a conseqüència directa dels punts anteriors, és important acabar el fil explicant, si no s'ha fet abans, com s'ha arribat a la solució del problema. De pas, aprofiteu per marcar el fil com a resolt [SOLVED].

Això ho podreu fer un cop us identifiqueu amb el vostre usuari i contrassenya i anant al damunt del fil, fent clic a "Thread tools" i marcant l'opció "Mark this thread as solved". Tingueu present que això només ho podrà fer qui ha creat el fil o un dels moderadors del fòrum.


---

### Post by pacocarrasco on 2009-07-25
> **papapep said:**
> Perfecte. Enhorabona per haver-te'n sortit ;-)

Ara [marca el fil com a resolt]("http://ubuntuforums.org/showthread.php?p=3687595#post3687595"), si us plau.
Hola  papapep
Tengo un modem vodafone k3565, que me han dicho que es igual que el k3520 y me falta instalar python-vmc-2.5.2-4, lo que pasa es que mi estructura SO es Ubuntu 8:04 amd64 y con ella da error ¿sabrías donde puedo descargarme el python-vmc para amd64? llevo varios días visitando paginas web y no hay manera de encontrarlo.
Gracias

---

### Post by SiscoGarcia on 2009-07-27
> **pacocarrasco said:**
> Tengo un modem vodafone k3565, que me han dicho que es igual que el k3520...

Hola pacocarrasco, benvingut al fòrum de l'equip d'usuaris d'ubuntu en català. Hi ha dues coses que hauries de tenir en compte, la primera és que, com pots haver comprovat, aquest és el subfòrum dels usuaris d'ubuntu en català, i per tant l'idioma que fem servir és el català; i la segona és que tot i que t'hagin dit que el mòdem és igual, pel que dius el model és un altre, per tant hauries d'obrir un nou fil. A més, estaria bé que et passessis pels fils [iniciàtic]("http://ubuntuforums.org/showthread.php?t=599965") i de [benvinguda]("http://ubuntuforums.org/showthread.php?t=562776"), així sabries com funcionem i ens coneixeríem una mica ;)

---

