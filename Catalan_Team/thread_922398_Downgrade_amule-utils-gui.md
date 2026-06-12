---
title: "Downgrade amule-utils-gui"
date: 2008-09-17
forum: Catalan Team
---

### Post by guillemsola on 2008-09-17
Hola a tothom,

des que vaig actualitzar a hardy el portàtil que no puc connectar amb l'amule-gui remot amb l'amuled del servidor debian que tinc sempre funcionant.

El problema sembla ser que és una incompatibilitat entre versions ja que resulta que a la versió estable de debian hi ha l'amule 2.1.3 i a la hardy i ha la versió 2.2.

Fins ara ho he resolt connectant amb l'amule-gui de windows mitjançant wine ja que no se com fer que el paquet amule-utils-gui instal·lat a hardy sigui la versió 2.1.3.

He provat a executar el binari de l'amule-gui d'un feisty (2.1.3) directament al hardy però tampoc funciona, suposo que hi ha més llibreries involucrades.

Hi ha alguna manera de fer un downgrade? Potser la solució passa per baixar les fonts del 2.1.3 i tornar-lo a compilar al hardy? Funcionarà o li crearé un conflicte mental al hardy?

Salut!

---

### Post by patrickfromspain on 2008-09-17
la idea de compilar el 2.1.3 no em sembla dolenta... simplement instal·la-la sota /usr/local i no crec que tinguis cap problema.

salut

---

### Post by guillemsola on 2008-09-17
De bojos, XD

No hi ha manera de compilar el paquet des de les fonts. 

Per sort meva l'he trobat al launchpad ja compilat per la 8.04 com un paquet deb, però resulta que no es pot instal·lar perquè falta la llibreria libcrypto++6 que no es troba disponible ni a l'arxiu del launchpad.

He provat a instalar el paquet amb dpkg amb l'opció que no comprovi les dependències i l'instal·la però després continua demanant la ditxosa llibreria.

Quant no pot ser, no pot ser...

Gràcies

---

