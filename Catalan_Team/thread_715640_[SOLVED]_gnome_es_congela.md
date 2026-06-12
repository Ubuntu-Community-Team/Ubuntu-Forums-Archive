---
title: "[SOLVED] gnome es congela"
date: 2008-03-05
forum: Catalan Team
---

### Post by bratac on 2008-03-05
Bones,

des de fa una temporada que el gnome se'm congela. És a dir, desapareixen totes les icones de la pantalla i si vull apagar, reiniciar, anar a qualsevol carpeta mitjançant Llocs fer qualsevol cosa m'he d'esperar moltíssim, de vegades ni esperant-me hores la cosa millora i he de tancar l'ordinador pel dret per a començar de nou. Em podeu dir com ho puc solucionar (amb instruccions detallades per que no en sé massa del tema terminal)?

Gràcies,

---

### Post by papapep on 2008-03-05
Amb un altre usuari passa igual, o només amb el teu? ( si no en tens altres, crea'l)

---

### Post by bratac on 2008-03-05
De moment el nou usuari no se'm congela i he obert un fitxer d'inkscape amb difuminats (que em sol fer anar l'altre usuari més lent). 

Com ho puc solucionar?

fins ara,

---

### Post by papapep on 2008-03-05
Doncs el que faria jo és crear-me un nou usuari i carregar-me l'antic (passant els documents personals abans, clar). Una prova que pots fer és  reinstal·lar l'ubuntu-desktop a veure si això ho soluciona.

Has tocat alguna cosa de configuració del Gnome, o has instal·lat o desinstal·lat KDE's o similars? Ho dic per intentar esbrinar d'on t'ha sorgit el problema.

A banda, has provat a actualitzar el sistema (aptitude upgrade)?
A vegades aquesta simple acció m'ha solventat problemes que m'havien sorgit, també, de manera espontània.

---

### Post by bratac on 2008-03-05
Bones,

Vaig instal·lar el Krita, a part d'això no he instal·lat res que no sigui mitjançant els repositoris normals d'ubuntu excepte el programa de pissarra digital interactiva que utilitzo que s'instal·la amb un autopackage.

L'actualització que em dius s'ha de fer per terminal?

gràcies!

---

### Post by papapep on 2008-03-05
Jo, com ja sabràs, acostumo a fer aquestes coses per terminal (tot i que es poden fer per entorn gràfic, però no em preguntis com):

```
sudo aptitude update
```

```
sudo aptitude safe-upgrade
```

---

### Post by bratac on 2008-03-05
Bones!

encara no he fet les actualitzacions (ho faré al vespre) però es que amb l'usuari nou em passa una cosa molt estranya. De tant en tant (aleatòriament) quan tanco la finestra del navegador (firefox) em tanca la sessió d'usuari automàticament...

Alguna idea per arreglar-ho?

Moltes gràcies!

---

### Post by papapep on 2008-03-05
Evidenment que amb poques pistes no sabem ni què s'ha d'arreglar, però...això teu fa pinta de problema de ram o de controlador de video o de targeta gràfica.
Jo faria un memtest unes quantes hores a la ram, canviaria la targeta gràfica per una qualsevol que tinguis per veure si fa el mateix i, finalment, verificaria quin controlador tinc instal·lat i si és el que em porta problemes.

---

### Post by SiscoGarcia on 2008-03-05
Ni que sigui off-topic, jo també faig anar el programa de pissarra digital interactiva però només amb windows; no l'he trobat per ubuntu. D'on l'has tret, bratac?

> **bratac said:**
> Bones,

Vaig instal·lar el Krita, a part d'això no he instal·lat res que no sigui mitjançant els repositoris normals d'ubuntu excepte el programa de pissarra digital interactiva que utilitzo que s'instal·la amb un autopackage.

L'actualització que em dius s'ha de fer per terminal?

gràcies!

Gràcies.

---

### Post by Miquel Ubuntero on 2008-03-06
Les indicacions de papapep les trobo molt bones, a més, si vols, des de Terminal executa "free" i veuràs com està l'us de memoria. Mira que tinguis en marxa la memoria swap.
Si no entens el que et diu, fes una captura i enganxa-ho aquí que t'ho mirem.
Salut!

---

### Post by bratac on 2008-03-06
Bones,

Pel que fa a la ram i les congelacions de moment tot bé, tot i que estic fent proves.


Referent a la pissarra, jo faig classes de pissarra digital SmartBoard (que de totes les que he provat són les millors, i la que em van posar era smart) Per a baixar-te el connector has d'anar aquí:

[http://www2.smarttech.com/st/en-US/Support/SBS/]("http://www2.smarttech.com/st/en-US/Support/SBS/")

és un  autopackage. Un cop instal·lat et pots baixar els paquets de català. Si tens qualsevol altre dubte, diga-ho.

fins ara.

---

### Post by SiscoGarcia on 2008-03-06
Val, potser és això.

```
Referent a la pissarra, jo faig classes de pissarra digital SmartBoard (que de totes les que he provat són les millors, i la que em van posar era smart)
```

Nosaltres tenim una interwrite de dotació, i no hem trobat cap possibilitat per Linux (no sé si per Linkat és possible, haurem de mirar-ho).

Moltes gràcies de tota forma.

---

### Post by bratac on 2008-03-06
Desconec com funcionen aquestes pissarres, però si vols sé que el programari de la smartboard funciona sobre qualsevol pissarra digital (el programa per a pintar-hi i tal) no crec que els drivers funcionin. Al web d'interwrite he vist que es pot baixar una versió per a ubuntu 6.06, suposo que ja l'haureu provada, si no he vist que està adaptada pera Linex i el linex en ubuntu, si no m'equivoco... Potser d'aquí a poc podreu utilitzar-la. 

Em sap greu no poder ajudar més...

fins ara,

---

