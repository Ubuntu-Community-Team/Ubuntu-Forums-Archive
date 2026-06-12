---
title: "[SOLVED] OpenOffice.org 3.0 i ubuntu 8.04"
date: 2008-11-19
forum: Catalan Team
---

### Post by SiscoGarcia on 2008-11-19
Estic posant a punt un flamant [dell mini9]("http://www1.euro.dell.com/content/products/productdetails.aspx/laptop-inspiron-9?c=es&cs=esdhs1&l=es&s=dhs") que ve de sèrie amb Hardy (i que de moment no vull actualitzar perquè no és meu) i amb l'OOo2.4 que sí que voldria actualitzar a OOo 3.0 però no he pogut (he intentat afegir al sources.list les línies que m'han funcionat amb Intrepid però amb Hardy no valen), sabeu com puc fer-ho?

Les línies que he afegit al sources.list són:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```

EDITO: Aquestes són les línies que diu al [launchpad]("https://launchpad.net/~openoffice-pkgs/+archive") que s'hi haurien d'afegir per Hardy, si bé és cert que diu que l'OOo 3.0 només és disponible per Intrepid :(

---

### Post by lpargemi on 2008-11-20
Hola

No puc aportar res de nou, només que a mi em passa exactament el mateix. Primer, per badar, tenia els repositoris de l'intrepid en un hardy, i es clar no m'actualitzava. Al canviar als repositoris suposadament bons, ha deixat de fallar, de fer res i no ha instal.lat ooo 3.0

Salut

Lluís

---

### Post by SiscoGarcia on 2008-11-20
> **SiscoGarcia said:**
> Les línies que he afegit al sources.list són:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu hardy main
```

Aquestes són les línies que diu al [launchpad]("https://launchpad.net/~openoffice-pkgs/+archive") que s'hi haurien d'afegir per Hardy, [COLOR="Red"]**si bé és cert que diu que l'OOo 3.0 només és disponible per Intrepid**[/COLOR] :(

Lluís, em temo que no té solució (esperem a veure què diuen els supers) i que d'alguna manera OOo 3.0 i ubuntu 8.04 són incompatibles, si volem OOo 3.0 hem d'actualitzar-nos a 8.10 i si volem 8.04 ens hem de quedar amb OOo 2.4 :mad:

---

### Post by jaume69 on 2008-11-20
Per **Google** he vist que hi ha algun **.deb** que funciona a **Hardy**,no sé..

---

### Post by indiosincracia on 2008-11-21
Posa l'enllaç jaume69, pel que fa als repositoris del Sisco tampoc m'han funcionat amb la Hardy, que en principi es LTS, en desconec el motiu però això ha de rutllar tard o d'hora.

---

### Post by Pablitus on 2008-11-21
Bones!

Jo el tinc instal·lat a Hardy, però en castellà, no he trobat el .deb en català.

Deixo [l'enllaç]("http://download.openoffice.org/other.html#ca")

Salut!

---

### Post by SiscoGarcia on 2008-12-08
Sembla que després d'un període de proves en què els repositoris del launchpad van deixar de funcionar, la cosa està solventada i ja és operatiu l'[enllaç al launchpad]("https://launchpad.net/~openoffice-pkgs/+archive"), no només per intrepid que és on hi ha hagut el problema, sinó que es pot fer servir el mateix enllaç per hardy. Llàstima que m'he actualitzat a intrepid ;)

---

