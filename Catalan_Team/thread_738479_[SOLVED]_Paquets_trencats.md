---
title: "[SOLVED] Paquets trencats"
date: 2008-03-28
forum: Catalan Team
---

### Post by Druiling on 2008-03-28
Em passa una cosa, a veure si em podeu donar un cop de ma.
Resulta que he instal.lat una aplicació per a per el panell aquest tan xulo que imita apple però que sembla ser que suporta gràfiques que el que es fa servir normalment no suporta, i la qüestió és que em salta l'estrelleta del synaptic i quan vaig a actualitzar em diu que no pot.
Vaig al synaptic i busco el que m'ha dit, paquets trencats i em surt el que us passo en una captura.
M'agradaria provar la utilitat aquesta, però em temo que si elimino el paquet trencat aquest, no podré fer-ho servir.
És una xorrada, però potser em podeu donar un cop de ma.
He vist un post d'en Satboy resolt que parlava més o menys d'això, però m'ha semblat que no era  el que jo busco.
En fi...
Bona nit!

---

### Post by menut on 2008-03-28
És realment necessari que hagis d'actualitzar-lo ? En cas afirmatiu, per què no et descarregues manualment el paquet (fitxer *.tar.gz) de la web del projecte i el compiles tu mateix ?

---

### Post by jodufi on 2008-03-29
menut: 
No ha d'actualitzar res, es vol instal·lar l'AWN. A més, baixar el paquet i compilar-lo és una cosa que no desitjaria a ningú, sobretot quan ja hi ha paquets compilats.

Druiling:
Per a instal·lar-lo, prova de seguir els passos que et diuen en la pàgina del projecte:
[http://wiki.awn-project.org/DistributionGuides](http://wiki.awn-project.org/DistributionGuides)
Aquests passos són:
[INDENT]Des d'un terminal:[/INDENT]
[INDENT][INDENT]sudo gedit /etc/apt/sources.list[/INDENT][/INDENT]
[INDENT]Al fitxer que s'ha obert, afegeix:[/INDENT]
[INDENT][INDENT]deb [http://ppa.launchpad.net/reacocard-awn/ubuntu/](http://ppa.launchpad.net/reacocard-awn/ubuntu/) gutsy main[/INDENT][/INDENT]
[INDENT]I finalment, des del terminal:[/INDENT]
[INDENT][INDENT]sudo apt-get update[/INDENT][/INDENT]
[INDENT][INDENT]sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr[/INDENT][/INDENT]

Tots aquests passos es poden fer gràficament amb el «Fonts de programari» i el «Gestor de paquets Synaptic», però l'explicació seria més llarga i no tindríem tanta informació si tens un problema.

A més seguint aquests passos aconseguiràs una versió més nova :)

---

### Post by lesergi on 2008-03-29
Hola a tots,

Se suposa que l'error et dona perquè intenta sobrescriure un fitxer ja existent al sistema, que el conté el paquet libawn0.

La solución es basa en desinstal·lar libawn0 i instal·lar libawn-bzr.

Desconec què és el paquet libawn0 i si es pot desinstal·lar, però si no comporta la desinstal·lación de cap dependència, pots provar.

Salut!

---

### Post by jaume69 on 2008-03-30
Jo crec que la solució és la que diu** lsergi.**

Pasa que la versió de launchpad no és la mateixa que la de Tuxfamily.però entre gustos...
Pel que veig ara hi ha:

-AWN versió Tuxfamily
-AWN versió Launchpad

Personalment em quedo amb la de Tuxfamily però no la puc instal·lar per conflicte de paquets o dependències(**libawn0**).I he agafat la de Launchpad.

P.D.Però també hi ha **Cairo-dock** que també està molt bé,només que no porta cap **Applet** extra.

---

### Post by Druiling on 2008-03-30
Hola tots, 

Entre instal.lacions i desinstal.lacions volent posar-me xorrades a la pantalla he petat la resolució de gnome. He estat funcionant tot el cap de setmana amb windows perquè tenia urgència d'entregar una cosa avui i no podia entretenir-me, però un cop enllestida, he arrencat altre cop i aquest amb kde i, sorpresa! em funciona tot superbé a kde exepte que quan arrenco l'ordinador, després de sortir el grub i seleccionar sessió, la pantalla se'm torna boja fins que carrega, la meva sorpresa, com dic, ha estat que en kde, ni pantalles gegants que no puc ni mirar ni res de res com en gnome, i a més no m'hi deixa fer res, no puc tocar la configuració de la pantalla ni canviant la gràfica que diu que detecta ni res.
En fi, un altre dels meus misteris.
Suposo que si això pertany a un altre fil, m'ho direu, si us plau.
Gràcies a tothom i bona setmana!!

---

