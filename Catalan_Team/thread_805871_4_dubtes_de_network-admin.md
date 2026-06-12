---
title: "4 dubtes de network-admin"
date: 2008-05-24
forum: Catalan Team
---

### Post by calbasi on 2008-05-24
Hola,

Jo tinc una ubuntu des de fa temps, al meu portàtil... Hi ha 4 dubtes
situacions que no sé com resoldre:

1) Normalment quan estic treballant en un puesto, per exemple casa de
mon pare, el portàqtil guarda la última configuració de wireless i quan
torno a obrir l'ordinador agafa la connexió sense problema (per més
comoditat les tinc "guardades". però fa poc vaig posar adsl de ya.com a
casa i cada cop que entro a l'ubuntu per defecte "no recorda" els
paràmetres de connexió i he d'anar al network manager
(/usr/bin/network-admin) per "recordar-li". Això no passa de ser una
nosa, però em comporta el problema número 2. (tot i això, no sé perquè
m'ho fa només en aquesta connexió... suposo que deu ser alguna opció de
ya.com o potser de la wifi en el seu router... és extrany... us sona?).

2) El problema del punt 1), a part de que no entenc perquè ho fa, és que
si la meva parella o el meu fill entren en els seus comptes, que no
tenen drets d'administració, doncs no es poden connectar (i com que no
poden executar el network-admin, doncs he d'estar jo amb ells, si no,
res...). He probat de donar-los permís via el fitxer /etc/sudoers
d'execució del fitxer /usr/bin/network-admin però no el poden
executar... suposo que aquest executable necessita accedir a altres
directoris que desconec i per això no rutlla...

Sabeu com puc resoldre això? Hi ha cap manera de donar permís a uns
usuaris normals perquè accedeixin a les connexions de xarxa?

3) I ja per acabar, he vist que quan instal·lo a algun amic / conegut
l'ubuntu l'applet de wifi  (nm-applet em sembla que es diu, oi?) és molt
maco... surten totes les inalàmbriques que "enganxa", i es molt fàcil
canviar d'unes a altres, etc. En canvi jo això ho veig d'una manera
"antiga"2, com sempre... com si les actualitzacions que faig al meu
ubuntu no em modifiquessin això... Algú té alguna idea de què pot
passar?

i 4) Aquesta, ja de propina, només és per dir-vos que també vaig provar
de resoldre tot plegat amb allò de "itinerància", però quan poso allò no
es connecta enlloc... Un altre misteri...

Algú em pot ajudar en algun d'aquests temes?

Merci!

---

### Post by lluisanunez on 2008-05-24
Per donar permisos d'administració als altres usuaris, ves a Sistema > Administració > Usuaris i grups, selecciona un usuari i clica a Propietats > Privilegis d'usuari, allà marca "administrar el sistema"
Pel tema de les connexions, caldria saber quina tarja de xarxa tens, i quina versió d'ubuntu.

---

### Post by calbasi on 2008-05-24
> **lluisanunez said:**
> Per donar permisos d'administració als altres usuaris, ves a Sistema > Administració > Usuaris i grups, selecciona un usuari i clica a Propietats > Privilegis d'usuari, allà marca "administrar el sistema"
Pel tema de les connexions, caldria saber quina tarja de xarxa tens, i quina versió d'ubuntu.

Home, la gràcia és que et puguis connectar a Internet sense haver de ser administrador... Ja sé que puc donar permís d'administració a tots els usuaris, però llavors això serà un maldecap, perquè qualsevol pot desconfigurar qualsevol cosa!! O sigui que no és cap sol·lució (o més aviat és una sol·lució tipus "windows").

Bueno, el problema de que "recordes" els paràmetres de configuració de la xarxa, o el que és el mateix, que arrenqués connectat, l'he resolt canviant la clau de la wifi del tipus wap al tipus wep. Suposo que això era una mena de bug a les configuracions de xarxa wap... El cost? Perdre el plus de seguretat que em donava wap per sobre de wep (segons tinc entés...), però com que tampoc espero tenir cap veí craker que em putegi :-)

---

### Post by oriolsbd on 2008-05-24
Hola, Calbasi.

En la mateixa opció de propietats dels usuaris, ves a la pestanya "Privilegis d'usuari" i marca les següents opcions:
Connexió a Intenet amb Modem
Utilització dels Modems

Funciona ara?

Salut!

---

### Post by calbasi on 2008-05-24
> **oriolsbd said:**
> Hola, Calbasi.

En la mateixa opció de propietats dels usuaris, ves a la pestanya "Privilegis d'usuari" i marca les següents opcions:
Connexió a Intenet amb Modem
Utilització dels Modems

Funciona ara?

Salut!

No :-( 

Els usuaris del meu ordinador tenen tots els permisos del administrador d'usuaris excepte el de "administrador"...

---

### Post by SiscoGarcia on 2008-05-25
> **calbasi said:**
> Home, la gràcia és que et puguis connectar a Internet sense haver de ser administrador... Ja sé que puc donar permís d'administració a tots els usuaris, però llavors això serà un maldecap, perquè qualsevol pot desconfigurar qualsevol cosa!! O sigui que no és cap sol·lució (o més aviat és una sol·lució tipus "windows").

Bueno, el problema de que "recordes" els paràmetres de configuració de la xarxa, o el que és el mateix, que arrenqués connectat, l'he resolt canviant la clau de la wifi del tipus wap al tipus wep. Suposo que això era una mena de bug a les configuracions de xarxa wap... El cost? Perdre el plus de seguretat que em donava wap per sobre de wep (segons tinc entés...), però com que tampoc espero tenir cap veí craker que em putegi :-)

No sé si una solució als dos problemes no podria ser configurar la connexió per filtratge de MAC-adress enlloc de fer-ho per wap o wep? Pots provar a veure què, no?

---

### Post by calbasi on 2008-05-26
> **SiscoGarcia said:**
> No sé si una solució als dos problemes no podria ser configurar la connexió per filtratge de MAC-adress enlloc de fer-ho per wap o wep? Pots provar a veure què, no?

Amb la contrasenya wep ja no tinc cap problema, però si, si vull afegir seguretat puc afegir un filtrat per mac... Això només té la pega de que si ve a casa algun amic amb el seu portàtil, etc. he d'obrir la xarxa amb el router (i si no estic jo a casa i està la meva parella, doncs res). Però realment no hi ha masses amics que vinguin a casa amb el portàtil i per fer-lo servir :-)

Salut!

Pd.: per cert, dels dubtes 3 i 4 alguna idea?

---

### Post by papapep on 2008-05-26
Jo provaria a crear un usuari nou i veure com li surt a ell. Jo no tinc igual el meu usuari (actualitzat un cop rera l'altre des del principi dels temps...:-)) que si en creo un de nou que sembla una instal·lació neta de Hardy...

---

### Post by calbasi on 2008-05-28
> **papapep said:**
> Jo provaria a crear un usuari nou i veure com li surt a ell. Jo no tinc igual el meu usuari (actualitzat un cop rera l'altre des del principi dels temps...:-)) que si en creo un de nou que sembla una instal·lació neta de Hardy...

Hola,

He creat un usuari nou, amb tots els permisos menys els d'administrador (usuari "desktop" que diu l'ubuntu).

I si faig la comanda:

- gksu network-admin no xuta, perquè després de demanar-me la contrasenya em diu que jo no tinc permís...
- network-admin no fa res (perquè no tinc permís)
- sudo network-admin tampoc funciona perquè el nou usuari no està al fitxer de sudoers... 

Pd.: això, amb l'ubuntu 7.10

---

