---
title: "Actualitzar versió aMule 2.1.3"
date: 2008-09-08
forum: Catalan Team
---

### Post by Curial on 2008-09-08
No sé si paga la pena però volia provar d'actualizar l'amule de la versió 2.1.3 a última.(encara treballo amb 7.10)

He mirat al gestor de paquets synaptic però únicament m'apareix la versió que ja tinc (2.1.3).

He baixat l'arxiu amule_2.2.2-1_i386.deb, el que no se si instal·lar-lo és la manera adient d'actualizar o si a més tinc el risc de trepitjar el que ja estic baixant amb l'amule i que està a mitges.

Què en penseu?

Salut

---

### Post by patrickfromspain on 2008-09-08
instal·les normal i ja esta, no tindras problemes.

salut

---

### Post by jaume69 on 2008-09-08
jo el tinc instal·lat (2.2.2) a través dels repositoris afegits **GetDeb**,des de Synaptic i me'l va actualitzar.
Suposo que no el va des-instal.lar.

A part d'això,funciona bé com l'altre,jo no hi veig moltes millores.
:confused:

---

### Post by Curial on 2008-09-09
Gràcies companys, però l'he instal·lat i ja no executa quan li dono a la icona de l'amule (aplicacions-internet-amule). Simplement no fa res.

Veig això sí, que a dins del synàptic ja apareix aquesta nova versió encara que diu que és un instal·lador per versions debian/ubuntu :confused: que vol dir això que encara no s'ha instal·lat?

---

### Post by patrickfromspain on 2008-09-09
prova d'executar-lo desde un terminal i posans que t'hi diu

salut

EDITO: aquestes coses poden passar amb paquets trets de ves a saber on, fets a saber de quina manera.

EDITO2: has instal·lat també la versió 2.2.2 del paquet amule-common?

---

### Post by Curial on 2008-09-09
> **patrickfromspain said:**
> prova d'executar-lo desde un terminal i posans que t'hi diu

salut

EDITO: aquestes coses poden passar amb paquets trets de ves a saber on, fets a saber de quina manera.

EDITO2: has instal·lat també la versió 2.2.2 del paquet amule-common?

En executar-lo des del terminal:
laia@laia-desktop:~$ amule
amule: error while loading shared libraries: libcrypto++.so.7: cannot open shared object file: No such file or directory

Referent a l'amule-common em té instal·lat la 2.1.3-3 :confused:

salut

EDITO: Per cert, abans d'instl·lar m'avisa: [I]"ha trobat una versió més antiga a un canal de programari
En general es recomana que instal·leu la versió del canal de programari, ja que normalment està millor mantinguda"
[/I]
On es pot trobar?

---

### Post by patrickfromspain on 2008-09-10
[http://www.getdeb.net/release/3047](http://www.getdeb.net/release/3047)

aqui hi veig els 2 arxius: amule y amule-common, has d'instal·lar-los els 2, primer el common.

A més, has d'instal·lar el paquet libcrypto++7, que es un dels error que et dona al obrir-lo

salut

---

### Post by Curial on 2008-09-10
Ho he estat mirant i no n'he tret l'entrellat.

Com s'instal·la la dependència libcrypto++7?

EDITO: Perdoneu, ja l'he trobat.

---

### Post by Curial on 2008-09-10
Instal.lo l'amule-common i em demana que faci un "sudo apt-get install -f", cap problema.
Instal·lo l'amule i no continua la instal·lació perque no tinc el libcrypto++7 (bé això ja ho sabiem).
Instal·lo paquet libcrypto++7 i no acaba la instal·lació que em diu que no és satisfactori el libc6.
Miro al synaptic i veig que si que el tinc instal·lat el libc6.

Ara ja si que me quedat clavat :(

---

### Post by patrickfromspain on 2008-09-10
El problema deu venir de que aquest paquests estan fets per a hardy i tu encara tens la gutsy (7.10). El libc6 que tens es una versio anterior, i alla es on deu ser el problema.

O busques un amule 2.2.2 compilat per a gutsy o t'el compiles tu mateix.

salut

---

### Post by Curial on 2008-09-12
Ok, moltes gràcies.

Provablement em sigui més fàcil actualitzar a la hardy.

Salut

---

### Post by patrickfromspain on 2008-09-12
ja posats, m'esperaria a la versio 8.10 (Intrepid Ibex). I mes posats encara, aprofitaria per posar una particio /home a part, si no la tens ja.

salut!!

---

