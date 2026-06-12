---
title: "[SOLVED] Formatejar unitats externes"
date: 2008-10-16
forum: Catalan Team
---

### Post by Josep Maria on 2008-10-16
Bona nit a totes i tots:
Estic mirant de formatejar un pen drive de 16 Gigues que acabo de comprar.
Està ple d'utilitats per a Windows que no faré servir, i voldria netejar-lo.
La única manera que se m'acudeix és de fer-ho amb l'editor de particions.
Hi ha algun programa o alguna altra manera de formatejar unitats des de linux?

---

### Post by papapep on 2008-10-16
L'editor de particions també forma part de Linux :-), en format gràfic clar.

Tu busques el mkfs. Per a formatar-lo a FAT32

```
sudo mkfs -t vfat /dev/sdXN
```

essent X la lletra de la partició i N el número, que vols reformatar.

Per cert, MOLT de compte amb no equivocar-te de partició, que el que formatis perd tot el que hi hagi....

---

### Post by Josep Maria on 2008-10-17
Perdona Papapep per la meva ignorància.

He estat mirant manuals per no molestar-te, però no m'arribo a aclarir.
Tu m'expliques que per formatar una unitat externa, en aquest cas un llapis de memòria cal fer :
"sudo mkfs -t vfat /dev/sdXN
essent X la lletra de la partició i N el número, que vols reformatar"

Però com puc saber quina és la lletra de la partició i el número que haig de formatar?
Si ho miro amb l'editor de particions em surt que la unitat es a /dev/sdb/ i sembla que la partició sigui la número 1 car només n'hi ha una : sdb1.
En aquest cas l'ordre correcta per formatar aquesta unitat seria sudo mkfs -t vfat /dev/sdb1 ?

Gràcies Papapep.

No feu mai cursets introductoris a Linux?

---

### Post by papapep on 2008-10-17
No cal disculpar-se per res.

Si la partició sdb1 que esmentes és el disc aquest extern, doncs sí. La ordre seria la correcta.

Pots esbrinar el nom de la partició sense haver d'arrencar l'editor de particions:

```
sudo fdisk -l
```

així veuràs totes les particions muntades. Si dubtes de quina és el teu disc extern, treu-lo, fes l'fdisk, torna'l a posar, torna'l a fer i veuràs quina unitat ha aparegut respecte el primer cop.

> 
No feu mai cursets introductoris a Linux? 

Doncs no, que jo sàpiga. Hi ha multitud de tutorials que ajuden en les coses bàsiques de Gnu/Linux. Potser en un futur, qui sap.
[A la meva signatura en pots trobar un]("https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes"). És una bona manera de començar.

---

### Post by _DarkEagle_ on 2008-10-17
Hola bon dia,

Quan insereixes el llapis USB automàticament Ubuntu te'l munta, a part del que diu el papapep que és molt correcte, també pots veure les particions muntades amb la comanda:

```
mount
```

a més ... també pots mirar el que ha passat al inserir el pendrive, així com on ha sigut el lloc de muntatge etc amb la comanda:

```
tail -f /var/log/syslog
```

Salut !

---

### Post by Josep Maria on 2008-10-17
Gracies als dos:
Efectivament la unitat era aquesta i l'he formatat bé.
Una pregunta encara, i si volgués donar a una unitat de disc dur extern el format ext3, quina seria l'ordre a escriure al terminal?

---

### Post by papapep on 2008-10-17
```
sudo mkfs -t ext3 blah, blah, bla...
```

o 

```
sudo mkfs.ext3 blah, blah, blah
```

:-)

si fas un cop d'ull a la pàgina del manual

```
man mkfs
```

explica algunes coses més.

---

### Post by Josep Maria on 2008-10-17
Coi Papapep, no sabia que hi havia aquest manual al terminal.
És fantàstic!
La veritat és que sempre li tinc una mica de pànic al terminal...
Gràcies.

---

### Post by papapep on 2008-10-17
> no sabia que hi havia aquest manual al terminal.

Doncs "man" és la mare dels ous, Josep Maria. Hi ha pàgines del man més o menys clares o afortunades, n'hi ha algunes de molt bones i d'altres un pèl justetes. Però per regla general són la millor font, en primera instància com a mínim, per a entendre com funciona una ordre. ;-)

> La veritat és que sempre li tinc una mica de pànic al terminal...

És normal, que no per això justificat. Ens ha passat a tots, però quan més t'hi fiquis, més veuràs que la seva potència és brutal i que la complexitat no és tanta com sembla "des de fora".

---

