---
title: "[SOLVED] Perdo les DNS"
date: 2008-07-18
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-07-18
Bones.
Tinc Ubuntu 7.10 amb un Routter D-Link model DSL-524T amb ya.com
Recienment han fet un canvi en el servei. Ara el tipus de conexió és "Ethernet", que no tinc gaire clar que vol dir.
El problema és que ara cada cop que reinicio el pc s'esborren les DNS's a l'entorn de xarxa i no puc navegar. En posar-les de nou va be. 
De moment les 2 trucades que he fet a ya.com no han servit de res, peró penso insistir amb élls.
De totes formes; li pasa algú més?
Sabeu quin problema puc tindre?
Moltes gracies.

---

### Post by Miquel Ubuntero on 2008-07-18
Hola de nou.
He fet probes amb un altre pc, i puc navegar correctament amb Ubuntu 7.10 sense posar les DNS's a configuració de xarxa. Per defecte a DNS hem surt la IP del Routter.
Però, cosa extranya, al pc de casa només navego posant-hi les DNS's. El problema, tal com ja he comentat, es que sen van en reinicar pc.
Es poden fixar d'alguna manera?
Gracies.

---

### Post by papapep on 2008-07-18
Les dns es desen a /etc/resolv.conf.

Jo havia tingut problemes amb al gnome-network-manager i em passava el mateix que tu expliques (el qual no vol dir que el teu problema hagi de ser el mateix). Jo ho vaig resoldre instal·lant el Wicd per a gestionar-me la xarxa i treient el gnome-network-manager. (Atenció: si algú té ganes de jugar a esborrar-lo, aneu amb molt de compte, que el sistema us proposarà desinstal·lar l'ubuntu-desktop al fer-ho! No us carregueu el sistema)

---

### Post by CarlesOriol on 2008-07-19
El que diu en papapep està bé però en qualsevol cas és una manca de configuració del router. 
Caldrà que et diguin com accedir-hi i un com allà canvies les dns per que quan t'ofereixi les adreces ip (dhcp) t'ofereixi també ip del router.

---

### Post by Miquel Ubuntero on 2008-07-19
Hola de nou.
Tal com deia en Carles, certament el problema estaba al Routter, tot i que era extrany donat que no afectaba al pc portatil :confused:

Dons be, he cercat dins el Routter i a la pestanya del DHCP he possat les DNS adecuades. A les hores ja puc reiniciar el pc tan com vulgui que ja funciona be.:)

Moltes gracies. Salut!

---

