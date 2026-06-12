---
title: "USB treballant en viu no detecta una partició"
date: 2008-04-29
forum: Catalan Team
---

### Post by Curial on 2008-04-29
Estic funcionant amb un portàtil amb l'ubuntu instal·lat a la USB en live i tinc dues particions ntfs, una per al hasefroch i l'altre per a rescat del sistema (altrament dita HP recovery), al disc dur.

A la partició petita, on hi ha arxius de recuperació del hasefroch si que hi puc accedir, muntar i desmuntar, en canvi no se per quin motiu de tot un plegat he perdut l'accés a la partició principal del disc dur on tinc els arxius que m'interessen.

---

### Post by menut on 2008-04-29
Tema de permisos ? En viu, l'usuari és root...

Prova a muntar-la via Terminal (i fica-la dins d'una carpeta a /media)

---

### Post by Curial on 2008-05-06
Hola Menut,

Bé crec que no es tracta de permisos. Ho he provat creant un altre usuari i l'he intentat muntar des del terminal i ha estat infructuós.

Em dóna la sensació que sona a allò tan estrany per a mi com és el punt de muntatge.

De fet només em cal inserir un llapis de memòria perquè aquesta partició funcioni bé, aquesta i el llapis, és clar. Si desconnecto el llapis, funciona fins que desmunto la partició en qüestió.


Aquest és el missatge:

---

