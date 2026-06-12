---
title: "[SOLVED] Amule no funciona"
date: 2008-03-24
forum: Catalan Team
---

### Post by kukat on 2008-03-24
Iep!
Doncs això, que no funciona el Amule. He provat eliminant-lo completament amb Synaptic, i tornant-lo a insta&#320;lar, però res, no troba res quan fas una cerca (però res de res)

Com teniu vosaltres la configuració de l'Amule? Quina llista de servidors utilitzeu? Per que jo he mirat en la web de l'amule i he fet el que diuen, i he posat la llista de servidors que ens donen (la que funciona, suposadament) però res de res. I els ports del router estan oberts....jo que se. L'Amule ha mort...jejejeje. En lo be que anava....:confused:

Salut!

---

### Post by menut on 2008-03-24
Se't connecta a algun servidor?
Recorda que necessites estar connectat per a poder buscar fitxers !

Prova actualitzant amb aquesta llista de servidors:

```
http://www.gruk.org/server.met
```

Pots revisar els ports amb Firestarter (intefície gràfice de iptables) amb un ```
sudo aptitude install firestarter
```

---

### Post by CarlesOriol on 2008-03-25
> **menut said:**
> Pots revisar els ports amb Firestarter

Amb el firestarter pots revisar els ports oberts al router?????? 	[-X
Crec que et confons.

---

### Post by kukat on 2008-03-25
Açò es el que hem surt quan es connecta l'amule, i pareix que tot estigui bé:

2008-03-25 11:21:38: El fitxer de crèdits ha estat carregat, 16574 són clients coneguts

2008-03-25 11:21:38:  - Aquest és l'aMule 2.1.3 using wxGTK2 v2.8.4 (Unicoded) basat en l'eMule.
2008-03-25 11:21:38:    Executant-se sobre Linux 2.6.22-14-generic i686
2008-03-25 11:21:38:  - Visiteu [http://www.amule.org](http://www.amule.org) per a comprovar si hi ha una nova versió disponible.

[I]2008-03-25 11:21:38: Carregant els fitxers ipfilter.dat.
2008-03-25 11:21:38: S'han carregat 0 rangs IP des de 'ipfilter.dat'. S'han descartat 0 línies malformades.
2008-03-25 11:21:38: S'han carregat 0 rangs IP des de 'ipfilter_static.dat'. S'han descartat 0 línies malformades.
2008-03-25 11:21:38: Carregant el fitxer server.met: /home/kukat/.aMule/server.met
2008-03-25 11:21:38: S'han trobat 23 servidors del server.met
2008-03-25 11:21:38: No s'han trobat parts
2008-03-25 11:21:38: Les connexions externes estan inhabilitades al fitxer de configuració
2008-03-25 11:21:38: MuleUDPSocket: Created Server UDP-Socket at port 4665
2008-03-25 11:21:38: MuleUDPSocket: Created Client UDP-Socket at port 4672
2008-03-25 11:21:38: S'han trobat 4 fitxers compartits
2008-03-25 11:21:38: Connectant
2008-03-25 11:21:38: Servers: Trying to connect
2008-03-25 11:21:38: Connectant amb United Server No1  (66.90.73.253 - 66.90.73.253:8899)
2008-03-25 11:21:38: Llegits 0 contactes Kad
2008-03-25 11:21:39: Fil AICH: Ha començat la sincronització del fil.
2008-03-25 11:21:39: Fil AICH: S'han carregat els hash mestres dels fitxers coneguts.
2008-03-25 11:21:39: Fil AICH: No s'han trobat fitxers nous.
2008-03-25 11:21:39: Fil AICH: Aturat.
2008-03-25 11:21:39: La vostra versió de l'aMule és l'última.
2008-03-25 11:21:39: Servers: Trying to connect
2008-03-25 11:21:39: Connectant amb United Europe 1  (85.17.208.77 - 85.17.208.77:8899)
2008-03-25 11:21:39: Connectat a United Server No1  (66.90.73.253:8899)
2008-03-25 11:21:39: Connectat a United Europe 1  (85.17.208.77:8899)
2008-03-25 11:21:39: Servers: Connected
2008-03-25 11:21:39: Connexió establerta amb: United Server No1
2008-03-25 11:21:39: La nova ID d'usuari és 2640067413[/I]

No encontra res, a no ser que no hi haja res d' Iron Maiden amb "Cerca Global"....:) (per posar un exemple)

---

### Post by menut on 2008-03-25
> **CarlesOriol said:**
> Amb el firestarter pots revisar els ports oberts al router?????? 	[-X
Crec que et confons.

Nooo, però pots saber si el iptables et bloqueja la connexió per software.

---

### Post by kukat on 2008-03-25
mmm....Insta&#320;le el Firestarter?? Recorde haver-lo insta&#320;lat una vegada, però no se....jo diria que els ports son oberts, ja que no ix la carassa a l'amule, i no diu res de Id Baixa...no se, es un poc estrany, la veritat...

---

### Post by papapep on 2008-03-25
> 2008-03-25 11:21:39: Connectant amb United Europe 1 (85.17.208.77 - 85.17.208.77:8899)
2008-03-25 11:21:39: Connectat a United Server No1 (66.90.73.253:8899)
2008-03-25 11:21:39: Connectat a United Europe 1 (85.17.208.77:8899)
2008-03-25 11:21:39: Servers: Connected
2008-03-25 11:21:39: **Connexió establerta amb: United Server No1**
2008-03-25 11:21:39: **La nova ID d'usuari és 2640067413**

Tens els ports perfectament oberts i funcionant. No toquis res del firestarter ni de l'iptables ni res d'això.

---

### Post by Daerun on 2008-03-25
Jo crec que el problema pot ser del servidor. Aquest a on et connectes no em sona de res, y és possible que sigui "pirata" o de pega (diuen que n'hi ha fins i tot de falsos que només existeixen per entorpir els p2p, però això ja no sé si és cert).

Fes el que t'ha recomanat en menut: esborra tots els servidors que tinguis, y actualitza la llista manualment desde:
[http://www.peerates.net/servers.php](http://www.peerates.net/servers.php)
o desde:
[http://www.gruk.org/server.met.gz](http://www.gruk.org/server.met.gz)

A part, tenint només tres fitxers compartits, és una mica difícil tenir una bona tasa de descàrrega. Baixa't unes quantes pel·lícules de les últimes estrenes, encara que no t'agradin, només perquè t'augmenti la càrrega.

---

### Post by kukat on 2008-03-25
Ok, funciona. Però jo el que feia era incloure els de "http://www.gruk.org/server.met.gz", però es veu que tenia que borrar els que hi havien abans d'incloure eixos... no sé....
En quant a lo dels arxius compartits, això ho arregle en un moment...jejeje:) Es que encara no els havia posat després de reinstalar l'amule...

Gràcies!!

---

### Post by Daerun on 2008-03-25
És clar, com que et connectaves a un servidor de pega, la cosa no tirava :lol: 
Ara mateix, els més estables son els diferents Razorbacks :wink:

---

