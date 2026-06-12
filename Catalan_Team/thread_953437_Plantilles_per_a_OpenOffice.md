---
title: "Plantilles per a OpenOffice"
date: 2008-10-20
forum: Catalan Team
---

### Post by kukat on 2008-10-20
Hola!
Per a quan la versió 3.0 en català?? (a la web oficial sols està la versió anterior) jo de moment estic gastant l'anglesa, i està molt molt bé!!! :)
Està per a l'Intrepid i per a la Hardy...Per al Gutsy estarà?

Gràcies!

---

### Post by Rubunter on 2008-10-20
> **kukat said:**
> 
I ja de pas....per a quan la versió 3.0 en català?? (a la web oficial sols està la versió anterior) jo de moment estic gastant l'anglesa, i està molt molt bé!!! :)

Gràcies!

Jo m'he instal·lat avui el 3.0 dels repositoris i ja el tinc en catala.

---

### Post by papapep on 2008-10-20
De quin repositori? :roll:
A mi no em surt pas disponible als "normals" (hardy main, multiverse, universe)...

---

### Post by Rubunter on 2008-10-20
> **papapep said:**
> De quin repositori? :roll:
A mi no em surt pas disponible als "normals" (hardy main, multiverse, universe)...

Perdó, tens raó, hauria d'haver especificat. Els repositoris que he dit no són els "normals", són:

```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```
```
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

---

### Post by papapep on 2008-10-20
Cap problema. Moltes gràcies ;-)

---

### Post by kukat on 2008-10-20
mmm....i amb el Gutsy Gibbon també em val fer-ho amb el repositori del intrepid??? hi haurà algún problema?? 
Gràcies! ups, crec que s'ha desviat un poc el tema..jejeje
Però be:) tot siga per l'OpenOffice.

---

### Post by climent on 2008-10-20
He resseguit els launchpad i només em surt en hardy i en intrepid.

---

### Post by lpargemi on 2008-10-20
Disculpeu-me per la meva ignorància però: si executo aquestes ordres

> **Rubunter said:**
> 
```
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```
```
deb-src http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main
```

què estic fent? Afegeixo aquest repositori a la meva llista, o bé actualitzo des del repositori sense més (o totes les anteriors o cap de les anteriors, com als exàmens en test)

Agraït

Lluís

---

### Post by Rubunter on 2008-10-21
Afegeixes les dues linies a la llista de repositoris:

```
sudo gedit /etc/apt/sources.list 
```

Aquí hi enganxes els dos repositoris del launchpad. Una vegada hagis guardat aquest fitxer:

```
sudo aptitude update
```

```
sudo aptitude upgrade
```

I ja hauria d'estar

---

### Post by lFossil on 2008-10-23
Perdoneu però he seguit el procediment i sembla ser que anat bé, però continuo tenint el OpenOffice 2.4 i no trobo el 3.0,

---

### Post by kukat on 2008-10-28
Segons Softcatalà:   Versió 3.0

Encara s'està treballant-hi. Està previst que es publiqui el 30 d'Octubre del 2008. 

[http://www.softcatala.org/wiki/OpenOffice.org](http://www.softcatala.org/wiki/OpenOffice.org)

Crec que podrem aguantar 2 dies:)

---

### Post by SiscoGarcia on 2008-10-28
I tant que podrem aguantar 2 dies,... però jo ja el tinc :)

---

