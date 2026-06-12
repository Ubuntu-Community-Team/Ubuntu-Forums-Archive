---
title: "Bisoncam"
date: 2008-01-02
forum: Catalan Team
---

### Post by Druiling on 2008-01-02
Hola tothom!
Mireu, tinc un problema que és que no sé com fer perquè em funcioni la càmera web (va integrada en el portàtil).
Segons windows, és una BisonCam USB 2.0. Ara no sé com veure-la i fer-la anar.
Suggeriments, si us plau?
Gràcies.

---

### Post by lluisalguero on 2008-01-03
Com que estic amb el mateix cas que tu...m'afegeixo al fil

---

### Post by orestesmas on 2008-01-03
Dir això a vegades és com no dir res. Les marques comercials no són rellevants, perquè darrere una mateixa marca a vegades hi ha més d'un xipset diferent (potser l'han canviat a mitja producció) o un mateix xipset el munten diferents marques. Potser per internet es pot trobar algun lloc que relacioni marca **i model** amb el xipset que hi ha a dins.

El més important és com reconeix l'ordinador aquest maquinari. Si és una càmera USB aleshores si et plau obre un terminal i envia'ns la sortida de l'ordre:
```
lsusb -v
```

No cal que envïis tota la botifarra que et sortirà. Si saps identificar la secció on s'identifica la teva càmera, n'hi haurà prou amb aquell fragment.

Un avís: Hi ha possibilitats (i no pas petites) que la teva càmera no estigui suportada pel nucli. Això és causat la majoria de vegades perquè el fabricant no vol publicar les interioritats de funcionament del xipset, i endevinar-ho no és una tasca fàcil (tot i que a vegades hi ha gent amb molta traça i paciència que ho aconsegueix per alguns xipsets, i aleshores es pot fer un driver que dóni suport a aquesta càmera).

O sia, que si no funciona, no en doneu la culpa a GNU/Linux.

---

### Post by pespin on 2008-01-03
En principi si no teniu res que funcioni com a placa de video i teniu el dispositiu /dev/video0, és senyal que el nucli el detecta ell solet. Si no s'han de buscar els drivers (s'hi n'hi han)

```
ls /dev/video*
```

---

### Post by Druiling on 2008-01-03
Hola, es això?.
Bus 004 Device 004: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300.

-------------------------------------------------------------------------------------------------

Pespin, la teva ordre dona això:
Password:
root@maria-laptop:~# ls /dev/video*
ls: /dev/video*: No such file or directory
root@maria-laptop:~#

Espero, gràcies.

---

### Post by torracastanyes on 2008-01-03
Males notícies:

[https://sourceforge.net/project/showfiles.php?group_id=185953](https://sourceforge.net/project/showfiles.php?group_id=185953)

---

### Post by orestesmas on 2008-01-03
Jo no seria TAN pessimista, el projecte està viu, té llistes de correu actives i un repositori SVN ([http://m560x-driver.svn.sourceforge.net/viewvc/m560x-driver/m560x/](http://m560x-driver.svn.sourceforge.net/viewvc/m560x-driver/m560x/)). Potser simplement van molt a poc a poc...

Per saber si tindràs sort o no, druiling, pots preguntar a les llistes de correu.

---

### Post by Druiling on 2008-01-04
Bé, gràcies a tothom!

---

