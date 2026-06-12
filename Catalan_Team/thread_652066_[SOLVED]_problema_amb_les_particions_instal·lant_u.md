---
title: "[SOLVED] problema amb les particions instal·lant ubuntu"
date: 2007-12-28
forum: Catalan Team
---

### Post by leper on 2007-12-28
Bones!! mestik instalant un ubuntu desde del live cd. Cuan arribu al pas per preparar les particions i clico endavant, em diu que no s'ha definit el sistema de fitxers arrel, que ho correigeixi des del menu de partició. adjunto un screenshot perque ho veieu. què he de fer per poder instalarlo??
gracies ;)

---

### Post by leper on 2007-12-28
per cert, vull instalar lubuntu a la particio 3 sense esborrar les altres.

---

### Post by papapep on 2007-12-28
Benvingut Ieper,

El teu problema és un error de concepte: a tot sistema Unix/Linux li cal que una de  les particions tingui com a punt de muntatge "/" (sense cometes), o sigui, el directori arrel dels sistema de fitxers (també conegut com a "root" - el qual cal no confondre amb el super-usuari de nom "root").
A banda, a no ser que et calgui per algun fet concret, jo formataria la partició (o particions) on s'ha d'allotjar el Linux com a ext3, que és una versió evolucionada, millor i més segura que no pas ext2.
Aleshores, et cal editar la partició que tu vulguis, i dir-li que el punt de muntatge ja no és /media/elquesigui, sinó "/" (sense cometes, clar).

---

### Post by leper on 2007-12-29
gracies!!! ja l'he instal·lat. soc nou en això de les particions i tal  ^^'

---

### Post by papapep on 2007-12-29
Cap problema, tots hem estat novells.
Però, per ser-ho cada cop menys t'aconsello un parell de lectures:

[http://extralinux.net/?q=node/6](http://extralinux.net/?q=node/6)
[http://extralinux.net/?q=node/30](http://extralinux.net/?q=node/30)

A internet n'hi ha moltíssimes més per si vols ampliar coneixements.

---

