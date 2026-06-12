---
title: "[SOLVED] alternatives a network-manager"
date: 2008-08-08
forum: Catalan Team
---

### Post by climent on 2008-08-08
En el fil que s'ha obert "problemes amb el wifi" comenteu un gestor de xarxes que es diu wicd com a alternatiu a network-manager. Jo utilitzo el rutilt perquè tinc un dispositiu ralink. No és que em vagi malament, però. Sabeu si el wicd dóna suport als xips ralink? Quin gestor em recomaneu?

---

### Post by papapep on 2008-08-08
Crec que sí, que el Wicd gestiona els ralink, ja que un dels mòduls que dóna com a opció als dispositius inalàmbrics és el "ralink legacy", a més del madwifi, el hostap, ipw, broadcom, ndiswrapper, atmel i wext (no em demaneu gaire més informació, de wifi rasco poquet...:-)).

---

### Post by patrickfromspain on 2008-08-10
quin driver fas servir exactament? ho dic perque en versions noves d'ubuntu, per al xipsets ralink es fan servir els drivers lliures, que funcionen bé amb el network-manager. 

Jo faig servir el wicd, i no ho tinc configurat com a ralink, sino a wext.

---

### Post by climent on 2008-08-10
a hores d'ara faig servir el rt73 (de serialMonkey) que vaig canviar pel rt73usb que incorpora Ubuntu, que segons vaig llegir no funciona gaire bé. Com a gestor utilitzo el Rutilt. A veure, de fet el rt73usb amb Network-Manager no és que em vagi malament, però se'm tallava la connexió i em donava poca qualitat de senyal. D'aquí els canvis a rt73 amb Rutilt. Atenent al comentari d'en Papapep, he provat el Wicd amb xip Ralink legacy, però no me n'he sortit i he tornat al què conec. L'únic que m'emprenya d'anar fent assaigs és, per exemple, que el Wicd m'elimina el Network-manager i me les he d'empescar per reinstal·lar-lo, i no sé si els altres aplicatius que esmenta en Papapep fan el mateix efecte.

---

### Post by papapep on 2008-08-10
Uh!? Jo només he parlat d'un programa, el Wicd. La resta de coses són els diferents mòduls wifi que gestiona per a la placa que tinguis al teu ordinador. :-)
Has provat a fer servir el wextpel Ralink com ha comentat en Patrick?

---

### Post by climent on 2008-08-13
He trigat a respondre per què volia anar sobre segur. A veure, jo tinc un dispositiu inal·làmbric D-Link DWL-G122, versió C1, que pel què he pogut saber, va equipat amb un xip Ralink rt73. Vaig llegir que el mòdul rt73usb que incorpora l'Ubuntu no funcionava, i que calia equipar el rt73 de la gent de serialmonkey, i que el programa que s'entenia millor amb aquest mòdul és el Rutilt, però que en instal·lar-lo et petava el network-manager (d'altra banda el rutilt, al menys en la versió actual, no permet deshabilitar la DHCP). D'aquí la meva primera necessitat d'una alternativa al network-manager.
Bé, què he fet? Doncs tornar totalment sobre les meves passes, i ara resulta que tinc el network-manager amb el rt73usb "de sèrie" funcionant a ple rendiment des de fa dos dies i, tal com tinc col·locat el dispositiu respecte de l'antena del router, amb una qualitat de 85/100.

Tanmateix, amb el Wicd no me n'he sortit (suposo que he d'utilitzar la versió Ralink Legacy, però això voldrà dir canviar al rt73 de serialmonkey, no?)

Off course, agrair els vostres comentaris i dir-vos que seguiré insistint amb el Wicd o altres; la qüestió és seguir aprenent.

---

### Post by patrickfromspain on 2008-08-13
Si fas servir el r73usb, amb el wicd a preferencies -> connector de wpa supplicant, has de tenir posat wext.

---

