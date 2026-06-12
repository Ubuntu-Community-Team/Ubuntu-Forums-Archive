---
title: "Desinstal·lar programes del wine"
date: 2008-07-11
forum: Catalan Team
---

### Post by Daerun on 2008-07-11
Vull desinstal·lar un programa que tinc al wine, concretament un photoshop, però a través del menú "Elimineu programes del wine" no aconsegueixo res, ja que el programa segueix al mateix lloc tal cual. Com ho hauria de fer?

---

### Post by lpargemi on 2008-07-11
Jo sempre que he desinstal.lat coses al wine ho he fet des del "uninstall.exe" que sol haver-hi al directori de cada un dels programes. No sé si hi és per al photoshop.

Ho faig des de la consola:


```
lluis@lluis:~/.wine/drive_c/Program Files/AdobePhotohop$ wine uninstall.exe

```

lluís

---

### Post by Daerun on 2008-07-12
Doncs no, no hi ha uninstall.exe del photoshop... Però és que, a més, no puc arribar més enllà de drive_c amb el terminal; per algun motiu, no em reconeix el path /home/daerun/.wine/drive_c/Program Files,  em diu que no existeix.

---

### Post by pespin on 2008-07-12
Això és perquè la carpeta "Program Files" té un espai entre mig, i segurament estàs fent:

```
cd Program Files 
```
En haver-hi un espai entre mig la terminal es pensa que Program i Files són dos argumetns diferents, i intenta entrar al directori "Program". Per a passar com a parametre un directori amb espais pots fer-ho de dues maneres:

```
cd "Program Files"
```
o bé
```
cd Program\ Files
```

---

### Post by lpargemi on 2008-07-12
Son els espais en blanc, que no solen anar massa bé

Fent [HTML]cd Pro* [/HTML] també s'hi arriba (si no hi ha més carpetes que comencin per Pro, es clar)

lluís

---

### Post by oriolsbd on 2008-07-12
Una altra opció molt útil és escriure: "cd Pro" i prémer el tabulador. Si només hi ha un directori que es digui així, te'l completarà. Si n'hi ha més d'un, prement el tabulador per segon cop et mostrarà totes les opcions.

Això també serveix per a fitxers (quan sigui amb comandes que no són el "cd", clar).

Salut!

---

