---
title: "Gutsy Gibbon: Error al compilar i error amb libpango"
date: 2008-03-21
forum: Catalan Team
---

### Post by Mitjons on 2008-03-21
Bones, feia temps que no tenia errors al Ubuntu. Però ahir vaig esborrar-ho tot i fer una instal·lació neta del Gutsy Gibbon i em van apareixer un parell

El primer és que no puc compilar res. 
[IMG]http://img518.imageshack.us/img518/2595/capturaxw7.png[/IMG]
Em surt això amb el configure. He tafanejat i el build-essential està instal·lat

El segon error és amb el libpango1.0-0. Em diu que "Dependency is not satisfiable" el cerco amb el synaptic i m'apareix instal·lat. El torno a re-intstal·lar per si les mosques però res

Parare boig:mad:

---

### Post by patrickfromspain on 2008-03-21
Per compilar, necessites els paquets de desenvolupament (-dev). Habilita els diposits deb-src al teu sources.list, sudo apt-get update i sudo apt-get build-dep pidgin i hauries de poder compilar-lo.

salut

---

### Post by Mitjons on 2008-03-21
El pidgin al final ho he intal·lat amb els deb de getdeb

El que passa és que no puc compilar res. No puc fer-ho amb el Evolution-RSS ni amb els extres del AWN i, bé no he baixat més programes ja que no em funcionaran :icon_frown:

---

### Post by patrickfromspain on 2008-03-21
si no et compila, es que no saps com fer-ho ;)

Com ja t'he dit, per a la majoria de coses necessites paquetes de desenvolupament, acabats en -dev. En el cas del libpango que no et  trobava, necesites tenir insta&#320;lat el libpango1.0-dev.

Si alguna cosa no et va, intenta ser més especific, ja que dir que "no em compila" no es sinonim de res, i no ajuda a diagnositcar el problema. Pero abans, es clar, el google t'hauria de marcar alguna direccion.

salut!

---

### Post by marcoil on 2008-03-21
> **Mitjons said:**
> El segon error és amb el libpango1.0-0. Em diu que "Dependency is not satisfiable" el cerco amb el synaptic i m'apareix instal·lat. El torno a re-intstal·lar per si les mosques però res

Parare boig:mad:

És diferent tenir instal·lat un paquet i tenir instal·lat els arxius per fer desenvolupament. Per exemple, per emprar el pango, has de tenir instal·lat libpango1.0-0, però per desenvolupar quelcom amb pango necessites libpango1.0-dev.

---

### Post by Mitjons on 2008-03-21
Del libpango ja tenia les -dev instal·lades així que fallava per altra cosa. tot i què sembla que ja no dona problemes. Ja que al final s'ha instal·lat el Pidgin amb deb. Dobleclicava i em deia allò del libpango.

Del tema de la compilació doncs compilar moltes coses no en se. No ho negarem. Però justament he anat a parar als dos programes que sempre que he reinstal·lat l'Ubuntu, per nova versió o el que sigui, son els primers que baixo. I fins ara no havien falla

---

### Post by Ferri on 2008-03-21
Que se t'hagi instal·lat el paquet *.deb no vol dir que tinguis resoltes les dependències que et faltaven. Els paquets *.deb ja estan compilats.
Amb un programa com el Pidgin el més pràctic és fer servir la versió dels repositoris d'Ubuntu i difícilment tindràs problemes.
Tot i això, és possible que si necessites algun programa molt concret, o fer servir alguna opció només disponible a una versió més nova que la dels repositoris, necessitis compilar-lo. No sé exactament on feies doble clic per compilar, però t'aconsellaria que si mai compiles res ho fessis des de la línia de comandaments.
Per cert, el msgfmt que diu que no troba és al paquet gettext (sudo apt-get install gettext).

---

### Post by Mitjons on 2008-03-22
No, a veure al principi el deb no s'instal·laven per la libpango. Després per casualitat si s'hi van instal·lar. Ningú ha parlat de dobleclicà i compilar res


El tema de la compilació és un altra problema. Simplemente no configuren res i si dimenen res ho miro i hi està instal·lat. Si reinstal·lo dona igualment error.

---

