---
title: "VirtualBox"
date: 2008-12-02
forum: Catalan Team
---

### Post by prostata on 2008-12-02
Si tinc instal·lat i funcionant ja el Windows XP en una altra partició, podria usar-ho amb VirtualBox o tendria que reinstalarlo tot?

És a dir: en aquestes condicions dites, puc instal-lar VB i fer anar indistintament Xp-Hardy...??

Gràcies i salutacions

---

### Post by PatrickVogeli on 2008-12-02
no, això que comentes no es pot fer. Has de crear una màquina virtual amb el virtualbox i instarl·lar-hi l'XP.

salut

---

### Post by open-pitu on 2008-12-02
Com diu en PatrickVogeli el que comentes no és possible. VirtualBox no serveix per arrencar un Sistema Operatiu instal·lat en una partició, sinó per virtualitzar un sistema operatiu des d'una imatge.
La idea és que a VirtualBox configuraràs quins recursos dones a la virtualització i a partir d'allà tindràs una màquina virtual (on podràs heredar configuracions). A continuació el que has de fer és instal·lar el sistema operatiu a la imatge que hagis seleccionat.

Personalment mai ho he provat des de Linux, sempre ha estat al revés (de windows virtualitzar Ubuntu), però no hi han masses diferències.

---

### Post by prostata on 2008-12-03
per tant, entenc que la propera vegada que per "casualitat" em "carregui" el disc primer hauria d'instal-lar Ubuntu i després sense XP si podrìa instal-lar virtualbox y l'XP???.

Gràcies

---

### Post by oriolsbd on 2008-12-03
No exactament. Ara mateix ja et pots instal·lar el VirtualBox, donar-hi d'alta una Màquina Virtual i instal·lar-hi Windows XP.

El que et comentava el Patrick és que no seria el mateix Windows que tens a l'altra partició (amb els mateixos programes que hi tinguis instal·lats, discos durs, etc.) sinó una "instància nova" de Windows XP on hauries d'instal·lar-hi tots els programes que necessitis, amb l'espai que li hagis assignat a la Màquina Virtual, etc.

---

