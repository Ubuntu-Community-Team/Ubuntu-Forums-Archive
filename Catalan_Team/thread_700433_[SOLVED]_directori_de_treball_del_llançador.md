---
title: "[SOLVED] directori de treball del llançador"
date: 2008-02-18
forum: Catalan Team
---

### Post by jaumety on 2008-02-18
Hola bones, 

  M'agradaria saber com especificar el directori de treball a un llançador. Quan el  genero només em surten les opcions: tipus, nom, ordre i observacions. A windows el que estic cercant seria “inicia a”.

Gràcies.

---

### Post by CarlesOriol on 2008-02-18
Fes un script

---

### Post by jaumety on 2008-02-18
... i que hi hauria de posar a l'script?

---

### Post by papapep on 2008-02-18
Entenc que si el que et cal és executar un programa invocant-lo des d'un directori concret, doncs a l'script hauràs de posar un cd fins on vols anar i des d'allà cridar l'executable posant el cami absolut (per a més informació: [https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#head-d01b99e9245eaf10cd99272522cb4eda43c6e1b7](https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes#head-d01b99e9245eaf10cd99272522cb4eda43c6e1b7)

Si et cal més ajuda ja ho diràs. Però estaria bé saber què et cal fer exactament per tenir tota la informació.

---

### Post by CarlesOriol on 2008-02-19
Amb el gedit 

[B]#! /bin/sh

cd /lacarpeta/osubcarpeta

nomdelprograma[/B]

Enregistres l'arxiu i amb damunt amb el butó dret fas propietats > permisos i marques execució.

Ara fes que el llançador cridi aquest arxiu. 

En qualsevol cas explica'ns que vols fer ja que com diu en papapep pot ser ho puguis fer d'una altra forma.

--------------------------------------------------------------------------------

> ... i que hi hauria de posar a l'script?

No em sap greu escriure-ho però crec que tu també has de posar una mica de part teva.

---

### Post by jaumety on 2008-02-19
Moltes gràcies, ja ho he solventat!!!.

El que no se és on posar [SOLVED]

---

### Post by lluisanunez on 2008-02-19
Al principi del fil, al menú "Thread Tools"

---

