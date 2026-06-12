---
title: "Com fer un check del disc dur?"
date: 2008-08-10
forum: Catalan Team
---

### Post by nickpage on 2008-08-10
Hola companys,

avui he tornat de les vacances, i el primer que he fet és engegar el meu ordinador. Quan arrancava ha fet un check de les particions del disc fins que ha petat, posava que tenia un error al disc i me deia que per continuar tenia que polsar CTRL + D. Després de fer-ho el ubuntu s'ha iniciat correctament i funciono sense problema. Però cada vegada que reinicio l'ordinador em surt el mateix error.

Hi ha alguna eina per poder corregir aquest error?

Gràcies

---

### Post by indiosincracia on 2008-08-10
Amb un CD-live, engegant l'ordinador amb el disc dur desmontat, fas correr e2fsck, fes-ho en varies ocasions, ara be, si comences a tenir un disc dur amb errors comença't a plantejar-te de comprar-ne un de nou.

Es que no s'hi pot anar de vacances...

---

### Post by nickpage on 2008-08-11
Al final he buscat per internet i he trobat la solució... 

espero que no torni a passar.

Per tal de que quedi constància del que he fet ho comento ara:

1) Iniciar l'ubuntu amb el recovery mode
2) Quan el check de l'inici peta el que he fet es un fsck de la partició que petava, concretament fcsk /dev/sda2, i contestar yes a totes les preguntes que m'han anat sortint.

He tornat a reiniciar i tot perfecte.

Salut

---

### Post by papapep on 2008-08-11
El que has fet tu és, bàsicament, el mateix que et deia de fer l'Idiosincracia. Únicament, que tu has fet servir l'eina del teu mateix disc dur i ell et deia de fer-la servir externa.

En tot cas, com ell ja t'ha advertit, si es torna a repetir el problema assegura't de tenir una bona còpia de les dades que t'importen del teu disc, ja que és un avís de que alguna cosa no va bé a nivell físic.

---

