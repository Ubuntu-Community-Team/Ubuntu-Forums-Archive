---
title: "Amarok 2.0!!!"
date: 2008-11-14
forum: Catalan Team
---

### Post by kukat on 2008-11-14
Algú em recomana l'Amarok 2.0??? Vull dir: Funciona correctament?? jejeje. Té molt molt bona pinta!
He vist al seu bloc que ja es troba (des d'ahir!!)
[http://amarok.kde.org/blog/](http://amarok.kde.org/blog/)

El millor reproductor!

edito:
Preciós!: [http://www.binaryelysium.com/images/Amarok_npr2.png](http://www.binaryelysium.com/images/Amarok_npr2.png).

---

### Post by oriolsbd on 2008-11-14
Hola, Kukat.

De l'Amarok 2 encara no ha sortit la versió definitiva. Suposo que no deu faltar molt, però convé tenir-ho en compte. Al principi, va tenir molts problemes (fins i tot a les primeres versions no sonaven les cançons) però ara, que està a punt de sortir la versió definitiva, sembla que ja està molt afinat.

La veritat és que a mi també m'agrada moltíssim (és un dels pocs programes de KDE que utilitzo en el meu escriptori Gnome), i tinc moltes ganes que surti ja la versió 2, però jo esperaré a la versió definitiva.

Si te'l vols instal·lar, suposo que et funcionarà bé, perquè està en fase de desenvolupament molt avançada.

---

### Post by kukat on 2008-11-14
Es veritat, que encara està en desenvolupament...:(
Bé, de moment he encontrar açò: [http://tuxpepino.wordpress.com/2008/05/07/neon-instala-y-mantiene-la-ultima-version-de-amarok-2/](http://tuxpepino.wordpress.com/2008/05/07/neon-instala-y-mantiene-la-ultima-version-de-amarok-2/)

per anar provant!! jejeje

---

### Post by kukat on 2008-11-15
He insta&#320;lat l'Amarok Project Neon (amarok-nightly), per fi!!

He tingut que insta&#320;lar [un paquet que feia falta]("http://packages.ubuntu.com/hardy/i386/libopenexr2ldbl/download") (almenys per a Intrepid Ibex). De moment funciona perfectament!!!

Els passos:
1. sudo gedit /etc/apt/sources.list
Afegir la línia: deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main

2. sudo apt-get update
3. sudo apt-get install amarok-nightly

Si al fer l'últim pas, falten llibreries,[ insta&#320;lar el paquet]("http://packages.ubuntu.com/hardy/i386/libopenexr2ldbl/download"). 

A veure quan trauen la versió definitiva!
Salutacions!

---

### Post by orestesmas on 2008-11-15
Jo ja fa alguns dies que el faig servir, i funciona perfectament. Vull dir que no m'ha petat.

Ara bé, com tota la resta del KDE, l'Amarok està essent sotmès a un procés de modernització brutal. Han reescrit moltes parts de zero, emprant una arquitectura molt més flexible. Com a resultat d'això, hi ha certes característiques de la versió anterior que que encara no estan implementades, i d'altres que s'abandonaran per tal de fer-les diferent o no fer-les.

A la [revista oficial]("http://amarok.kde.org/Insider/Issue_13") pots trobar una llista dels canvis presents i futurs.

---

### Post by SiscoGarcia on 2008-11-15
> **kukat said:**
> He insta&#320;lat l'Amarok Project Neon (amarok-nightly), per fi!!

He tingut que insta&#320;lar [un paquet que feia falta]("http://packages.ubuntu.com/hardy/i386/libopenexr2ldbl/download") (almenys per a [COLOR="Red"]Intrepid Ibex[/COLOR]). De moment funciona perfectament!!!

Els passos:
1. sudo gedit /etc/apt/sources.list
Afegir la línia: deb [http://ppa.launchpad.net/project-neon/ubuntu](http://ppa.launchpad.net/project-neon/ubuntu) hardy main

2. sudo apt-get update
3. sudo apt-get install amarok-nightly

Si al fer l'últim pas, falten llibreries,[ insta&#320;lar el paquet]("http://packages.ubuntu.com/hardy/i386/libopenexr2ldbl/download"). 

A veure quan trauen la versió definitiva!
Salutacions!

Kukat, em sembla que t'has equivocat de versió quan dius que et cal un paquet al menys per [COLOR="Red"]Intrepid Ibex[/COLOR], pel que es veu a l'enllaç i per la línia que hi afegeixes, hauria de dir [COLOR="Red"]Hardy Heron[/COLOR], no?

---

### Post by kukat on 2008-11-16
:confused:No he trobat altra forma de fer-ho...mmm....[Hi havia una altra opció]("http://amarok.kde.org/blog/archives/833-Installing-Amarok-2-from-SVN-in-your-home-directory.html"), al bloc d'Amarok, però després d'intentar-ho un parell de vegades, no vaig aconseguir que s'insta&#320;lara.... Fent-ho com ho he posat si que m'ha funcionat. Vols dir que la línia deuria de ser dels repositoris de l'intrepid? 
Salutacions!

---

### Post by SiscoGarcia on 2008-11-16
Suposo que sí, kukat, el que passa és que no tinc gaires coneixements. Però com que el fitxer [existeix per a intrepid]("http://ppa.launchpad.net/project-neon/ubuntu/dists/intrepid/main/"), crec que la línia a afegir al sources.list seria:

```
deb http://ppa.launchpad.net/project-neon/ubuntu intrepid main
```

En qualsevol cas pots fer-te còpia del sources.list i provar-ho a veure què, o bé esperar confirmació per part dels que en saben ;)

---

### Post by oriolsbd on 2008-11-16
Hola, jo ho vaig fer com diu el SiscoGarcia en una màquina virtual, i la instal·lació m'ha donat un error, perquè diu que hi ha un fitxer que està en dos dels paquets d'amarok-nightly. He obert un bug al Launchpad ([https://bugs.launchpad.net/project-neon/+bug/298474](https://bugs.launchpad.net/project-neon/+bug/298474)).

Salutacions.

---

### Post by kukat on 2008-11-18
Doncs després d'uns dies de provar-lo, crec que em quedo amb l'anterior. Em sembla que la versió nova va un poc....M'agraden algunes coses, però altres encara les queda un poc. Ja se que es una versió beta, però em sembla més intuïtiva la "interface" de l'antic que aquesta...:) Té molt bones idees, però crec que se n'han passat amb el canvi radical de pràcticament tot!!! 
Bé, temps al temps!

---

