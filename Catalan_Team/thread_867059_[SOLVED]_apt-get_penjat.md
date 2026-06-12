---
title: "[SOLVED] apt-get penjat?"
date: 2008-07-22
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-07-22
Bones.
Fa un parell de dies, mentres estaba instal·lant  suport d'idioma es va penjar.
Des de aquest moment ara no puc fer servir apt-get ni Synaptic.

Seguint les recomanacions que el mateix Ubuntu 7.10 hem dona us mostro el que he fet. De "Generating Locales..." no passa, es queda "fregit".

root@lourdes-desktop:~# apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@lourdes-desktop:~# apt-get upgrade --fix-missing
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
root@lourdes-desktop:~# dpkg --configure -a
S'està configurant language-support-es (1:7.04+20070209) ...
Generating locales...
  es_AR.UTF-8... 


Es pot arreglar?

---

### Post by perlluver on 2008-07-22
```
sudo dpkg --configure -a
```

---

### Post by Miquel Ubuntero on 2008-07-22
Hola perlluver.
No acabo d'entendre que vols dir.
El que suggereixes ja ho habia fet:

root@lourdes-desktop:~# dpkg --configure -a
S'està configurant language-support-es (1:7.04+20070209) ...
Generating locales...
es_AR.UTF-8... 

Nomès que sense el "sudo" perque era "root" user

i d'quí no pasa, es queda com penjat.

Salut!

---

### Post by papapep on 2008-07-22
Dues coses: 

 - Enganxa el contingut del teu /etc/apt/sources.list

 - Fes un 

 ```
sudo apt-get install -f
```

a veure què diu.

Quan dius que "es queda penjat" el *dpkg --configure -a* quanta estona esperes?

També t'aconsellaria fer servir l'aptitude en vers de l'apt-get (excepte en casos d'operacions especials, com ara) ja que controla millor les dependències.

---

### Post by papapep on 2008-07-22
Tot i que acabo d'aconsellar fer servir aptitude abans que apt-get, com que és una eina molt important, sobretot en cas de problemes :-), he fet una pàgina al wiki amb un petit tutorial: [https://wiki.ubuntu.com/CatalanTeam/Recursos/GuiaRapidaApt-Get](https://wiki.ubuntu.com/CatalanTeam/Recursos/GuiaRapidaApt-Get), per a qui interessi o li faci falta.

---

### Post by manelfus on 2008-07-23
hola  tambe a mi m'ha passat la solucio esta en booteja desde el kernel anterior (el 14  crec) fent el sudo dpkg --configure -a i els locals podran actualitzarse

[http://ubuntuforums.org/showthread.php?t=865679](http://ubuntuforums.org/showthread.php?t=865679)

---

### Post by Miquel Ubuntero on 2008-07-24
Hola de nou.

Bona la d'en manel. He fet el mateix que tú i ja funciona tot be.

També bona la d'en Papapep, hem refereixo a la guia ràpida d'apt-get. Amb el teu permís aprofitare per ampliar la meva guia.

Moltes gracies a tots dos.

Salut!

---

### Post by oriolsbd on 2008-07-24
Papapep: molt bo, lo de la vaca. Només com a comentari, es pot fer aparèixer sense ser superusuari. És a dir, no cal fer-ho amb "sudo". :)

Pot ser un forat de seguretat de l'apt-get??? :lol:

---

### Post by papapep on 2008-07-24
> Pot ser un forat de seguretat de l'apt-get??? 

Ostres, quina cagada del desenvolupador d'apt-get...:-P

Això amb aptitude no passa...proveu, proveu a fer "aptitude moo"...és una eina més seriosa.

Fins i tot, podeu provar a fer "aptitude moo -v" (v vol dir "verbose", que xerri més), i veure-ho què us diu...que no en té...i aneu afegint "v" darrera la primera "-v" :-)

---

### Post by guillemsola on 2008-07-25
Hola,

fa poc vaig estar mirant el tema i em va semblar que era millor fer servir aptitude que apt-get, es veu que fa les coses molt millor i controla més eficaçment les dependències i coses així...

És veritat aixó? Ho dic perquè veig que tots feu servir l'apt-get.

Salut!

---

### Post by papapep on 2008-07-25
Al post núm.4 d'aquest mateix fil:

> També t'aconsellaria fer servir l'aptitude en vers de l'apt-get (excepte en casos d'operacions especials, com ara) ja que controla millor les dependències.

:-)

---

### Post by guillemsola on 2008-07-25
Vaja... he llegit massa ràpid. :confused:

De totes formes gràcies per l'aclaració.

Tornant al tema de la vaca, comenten en una web que un usuari ha presentat un bug al launchpad perquè diu que la vaca no sembla tal cosa...

[https://launchpad.net/ubuntu/+source/apt/+bug/56125](https://launchpad.net/ubuntu/+source/apt/+bug/56125)

Salut!

---

### Post by papapep on 2008-07-25
El bug, evidentment, és una parida i representa el temps que li sobra a segons qui, però els comentaris del bug no tenen desperdici :-D:-D:-D

---

