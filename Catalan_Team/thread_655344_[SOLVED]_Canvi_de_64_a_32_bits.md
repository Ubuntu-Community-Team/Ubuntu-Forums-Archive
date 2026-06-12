---
title: "[SOLVED] Canvi de 64 a 32 bits"
date: 2008-01-01
forum: Catalan Team
---

### Post by Joan Marc on 2008-01-01
Hola a tothom,
He pensat de treure l'Ubuntu que tinc ja que és 64 bits.
He vist que en papapep va penjar uns fils de les versions catalanitzades de l'ubuntu 7.10.
Un cop estic al fil, quin arxiu m'he de descarregar? (de l'ubuntu n'hi ha 5)
Hi ha cap fil que em digués com es fa per desinstal·lar l'ubuntu?

Moltes gràcies!

---

### Post by papapep on 2008-01-01
Si el que pretens és símplement instal·lar la versió de 32 bits damunt la de 64, doncs el que cal fer és dir-li que s'instal·li a les particions que ja tens creades pel sistema que tens actualment. Si, a més, li dius que et formati les particions encara faràs més net. No té més secret.

---

### Post by Joan Marc on 2008-01-01
Si no les formato, es borraran tots els documents igualment?
Una cosa, funcionarà el de 32bits al meu ordinador Intel Core2 Duo? 

Gràcies!

---

### Post by SiscoGarcia on 2008-01-01
[HTML]Una cosa, funcionarà el de 32bits al meu ordinador Intel Core2 Duo?[/HTML]Evidentment que et funcionarà el 32 bits amb un Intel Core2 (jo l'estic fent anar ara mateix), de fet la versió 64 bits és exclusiva pels AMD 64 bits.

---

### Post by SiscoGarcia on 2008-01-01
```
Una cosa, funcionarà el de 32bits al meu ordinador Intel Core2 Duo?
```Evidentment que et funcionarà el 32 bits amb un Intel Core2 (jo l'estic fent anar ara mateix), de fet la versió 64 bits és exclusiva pels AMD 64 bits.

---

### Post by papapep on 2008-01-01
> Si no les formato, es borraran tots els documents igualment?

Doncs si. Però per conservar els documents només els has de desar en un dvd o en una altra partició, depenent del volum de dades que tinguis.
Per que no et torni a passar, ara que ho refàs tot, potser seria el moment de fer una partíció pròpia pel /home a fi de minimitzar l'efecte de possibles properes reinstal·lacions o actualitzacions.

> Una cosa, funcionarà el de 32bits al meu ordinador Intel Core2 Duo?

Ja t'ha contestat en Sisco.

---

### Post by hakd0c on 2008-01-02
> **SiscoGarcia said:**
> [HTML]Una cosa, funcionarà el de 32bits al meu ordinador Intel Core2 Duo?[/HTML]Evidentment que et funcionarà el 32 bits amb un Intel Core2 (jo l'estic fent anar ara mateix), de fet la versió 64 bits és exclusiva pels AMD 64 bits.

Ostres això si que es una animalada, la versió 64 bits funciona amb la majoria de sistemes a 64bit entre ells els xeon, opteron i els core 2 duo, no així els core duo ja que aquests no son a 64bits.

Per si de cas jo li tinc instal·lat tant amb AMD com amb Intel i em va perfecte

---

### Post by Joan Marc on 2008-01-02
Gràcies a tots!!
Pel que fa a la pregunta de si em funcionarà ho he demanat perquè a la pàgina de descàrrega posava el de l'imatge adjunt.

> Per que no et torni a passar, ara que ho refàs tot, potser seria el moment de fer una partíció pròpia pel /home a fi de minimitzar l'efecte de possibles properes reinstal·lacions o actualitzacions.

Què vols dir? una partició a part de la de /(root) i la swap?


hakd0c, vull canviar a 32 bits pel què fa a programes i això, no perquè no em funcioni! Una cosa, que no l'he acabat d'entendre, dius que no funcionara la de 32 bits al meu ordinador o que la de 64 bits no és nomès per AMD 64 bits?

Salut i gràcies!

---

### Post by pespin on 2008-01-02
> Què vols dir? una partició a part de la de /(root) i la swap?

Sí, d'aquesta manera quan reinstal·lis la majoria de modificacions que tens les seguiràs tenint, ja que en molts casos es guarden en fitxers ocults a dins la teva carpeta home :)

---

### Post by Joan Marc on 2008-01-02
Així doncs, a la partició /home què s'hi guardarà?

---

### Post by papapep on 2008-01-02
Fes un cop d'ull a aquests dos articles:

[http://extralinux.net/?q=node/6](http://extralinux.net/?q=node/6)
[http://extralinux.net/?q=node/30](http://extralinux.net/?q=node/30)

---

### Post by Joan Marc on 2008-01-02
Ja m'ho havia llegit per sobre alguna vegada... així que si faig una partició /home, tot el que tinc de home de la partició / estarà a la partició /home no?

Tornant al tema de l'ubuntu en català, quin o quins arxius m'he de descarregar, a part de la ISO més actual, hi ha dos arxius amb extensió md5 i sha1, que obrint-los amb el gedit nomès contenen combinacions de lletres i números.  Que aquests dos arxius són com l'"autorrun" del Windows?

Gràcies:)

---

### Post by torracastanyes on 2008-01-02
Que aquests dos arxius són com l'"autorrun" del Windows?

Em penso que no.
Aquests arxius md5 i sha1 són sumes de verificació, per saber si la imatge ISO que has baixat és bona o té errors.

Mira't això:

[http://es.wikipedia.org/wiki/Md5sum](http://es.wikipedia.org/wiki/Md5sum)
[http://es.wikipedia.org/wiki/SHA1SUM_(fichero](http://es.wikipedia.org/wiki/SHA1SUM_(fichero))

Si utilitzes el k3b per a grabar les ISO, ell mateix et fa la md5sum abans de començar.

---

### Post by Joan Marc on 2008-01-04
Ja l'je gravat amb el k3b, i ha anat bé.
La partició de /home, quan ha d'ocupar respecte la / (36GB)?

Gràcies!

---

### Post by papapep on 2008-01-04
Tant com tu vulguis. Pensa que aquí es on hauries de desar tots els teus fitxers. Aleshores, en funció de la teva activitat (música, vídeo, jocs o només treball amb fitxers petits) sabràs si et cal molt d'espai o no. Però vaja, si li dones la resta de l'espai del disc dur ja fas el fet :-)

---

### Post by Joan Marc on 2008-01-07
De fet, la resta d'espai el tinc en una partició finestrosa, la qual tinc uns 40GB lliures.
No sé si redimensionar la partició finestrosa, i així poder fer la /home més gran, o deixar-la com està, i fer la /home i la /  de 18GB cadascuna.

Gràcies :)

---

