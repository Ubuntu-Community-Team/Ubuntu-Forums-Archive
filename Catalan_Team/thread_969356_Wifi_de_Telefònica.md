---
title: "Wifi de Telefònica"
date: 2008-11-03
forum: Catalan Team
---

### Post by catximba on 2008-11-03
bones!

a un altre fil m'han dit que obrís un fil nou per explicar el meu problema, i així ho faig.

Tinc un receptor wifi usb, d'Amper, distribuit per Telefònica.
la solució fins ara era l'ndiswrapper, perquè al Hardy me'l detectava, però a aquest em dóna problemes, no sé per què pot ser.

resulta que ara mateix funcione amb un altre receptor wifi amb què no puc detectar la meua xarxa, perquè està protegida de tot.

el driver en qüestió del receptor de telefònica és anomenat "prisma02.sys" instal·lat amb el "prisma02.inf"

teniu idea de què pot passar al meu ordinador o al meu sistema operatiu? (jo per instal·lar-lo vaig formatar i instal·lar, perquè a l'actualització em va donar problemes)


moltes gràcies de bestreta!

---

### Post by blauigris on 2008-11-14
Osti!, la de hores que m'he passat jo pegant-me amb aquest wifi! Quins bonics records. Bé, et diré un parell de coses de memoria.

Tot això es per fer-lo funcionar amb el driver natiu, amb les avantatges que això suposa: funciona de conya, mode ad-hoc i monitor, injecció, etc... Ara bé configurar-ho, si es que ho aconsegueixes és un auténtic conyàs, per tant, si portes poc temps amb això millor intenta arreglar el ndiwrapper. Sinó aqui et deixo fins on vaig arribar:

Primer, el wifi, malgrat que a sota posi amper, es de la marca Senao. Però el xipset que porta a dins (que és el que importa), es un prismgt que també s'anomena prism54, fabricat per Intersil. Hi han tres tipus de targetes que porten aquest xip. Les pci, les usb generació 1 i les usb generació 2. La que tens es de generació 2. Utilitza un firmware que es diu softMAC.

Ara et parlo del que vaig averiguar fa un parell mesos, o sigui que pot ser que s'hagi arreglat. Hi ha un driver natiu que sembla que va de conya amb les targetes que son pci i de primera generació, però encara no està del tot suportat per les de segona i almenys jo no vaig aconseguir fer-la funcionar. El trovaràs a la pagina [www.prism54.org](www.prism54.org), encara que em sembla que l'han canviat. Hi ha un lloc on posa les targetes suportades. Et diria si ho està o no, però la meva la té un amic i no recordo quin identificador tenia, així que hauràs de fer un lsusb a la consola, i et sortirà l'identificador. En principi està suportat, però té un altre nom (no se que d'Spinakker, com els barcos), i li has d'anar provant amb diferents versions de firmwares. Sigui com sigui a mi no em va funcionar.



Per lo del ndiswrapper, jo faria a consola un lsmod | grep ndiswrapper , per veure si està carregat el mòdul, pot ser que al reinstalar se't hagi tret del etc/modules i no el carregui per defecte. També faria un ndiswrapper -l (em sembla que era així, assegurat'en fent el mateix però amb -h) per saber si està el driver instalat. No se'm acut res més.

---

### Post by catximba on 2008-11-15
ara, per a tindre internet, m'he tornat a passar a windows, però he deixat una partició lliure per a ubuntu, tornaré a instal·lar el nou ubuntu, el 8.10, i a veure si aconseguisc això.

gràcies per la classe teòrica, total porte des de fa mig any amb ubuntu, o siga que encara no m'he adaptat del tot :P

---

