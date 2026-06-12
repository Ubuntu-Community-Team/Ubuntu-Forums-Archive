---
title: "Problema amb l'instal·lació de l'Alien Arena"
date: 2008-07-21
forum: Catalan Team
---

### Post by lo gambusí on 2008-07-21
Salut!!

Estic instal·lant l'Alien Arena. Descarrego de GetDeb els arxius alien-arena-data i alien-arena, instal·lo sense problemes el data però l'altre em diu el següent missatge:
> error: dependency is not satisfiable: libcurl3-gnutls

Miro el synaptic i la tinc instal·lada. La reinstal·lo i seguix donant-me el mateix error....

algú sap què puc fer?

gràcies!!!

---

### Post by LitusMayol on 2008-07-21
No sé si serà d'ajuda...

Jo faria
```
sudo aptitude purge alien-arena
```

I després sense els paquets directament per terminal
```
sudo aptitude install alien-arena
```

Jo el vaig instal·lar directament desde terminal i em funciona...


No sé si ha sigut molt útil...

---

### Post by lo gambusí on 2008-07-21
i un cop fet això com l'inicio? perquè fent alien-arena al terminal no em va...

---

### Post by LitusMayol on 2008-07-21
Jo l'obro anant a *Aplicacions>Jocs>Alien Arena*. 

A veure si pots... :S

---

### Post by jaume69 on 2008-07-21
Prova a instal.lar aquesta llibreria **[[COLOR="Red"]libgtk1.2[/COLOR]]("http://www.ubuntugames.org/AlienArena")**,pot ser et funciona.

Aquesta versió d'**Ubuntugames** no l'he provada.

Jo jugava amb **Alien** i crec que la versió de **GetDeb** és millor,o igual a la dels repositoris...,entre gustos..

(Ara que,si ja has instal.lat la dels **repos**,deixo així)
__________________________
No us vicieu...!!:)

---

### Post by lo gambusí on 2008-07-22
Ja he instal·lat l'libgtk1.2 i segueix sense engegar-se'm...

Ah, i lo joc no m'apareix, a Aplicacions/Jocs...:confused:

---

### Post by Miquel Ubuntero on 2008-07-22
Hola company.
Si ho has intal·lat tal com jo ho vaig fer, per iniciar joc des de Terminal executa "alienarena2006".

Si vols veure com ho vaig instal·lar, mirat la "Guia Ubuntu 7.04" que trobaras al meu blog [http://miquel66.caliu.cat](http://miquel66.caliu.cat) (pàgina 19 del manual).

Ah! si vols, fes un cop d'ull (a la mateixa guia) al joc Tremulous, tambè està prou be.

sort i molta diversió ;)

---

