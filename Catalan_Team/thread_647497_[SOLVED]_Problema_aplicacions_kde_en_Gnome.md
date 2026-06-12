---
title: "[SOLVED] Problema aplicacions kde en Gnome"
date: 2007-12-22
forum: Catalan Team
---

### Post by ernestux on 2007-12-22
Hola a tothom,

Tinc ubuntu gutsy entorn Gnome, amb alguna aplicació de kde i jo com a usuari primer principal no tinc cap problema.
Vaig crear una usuària nova amb drets d'administració i tot, però sovint en obrir les aplicacions de kde tipus  khangman, kanagram, klettres , etc. , s'obre l'aplicació però amb grandària de les lletres enorme (més de 60 ) cosa que fa no es puguin usar. Algun cop que entra l'usuària nova sí que estan les aplicacions kde ben configurades. Alguna idea ?  Només passa amb l'usuari creat nou. 

Gràcies,

---

### Post by orestesmas on 2007-12-22
L'aspecte de les aplicacions KDE s'estableix des del seu centre de control. Jo provaria d'executar-lo des d'un terminal (es diu "kcontrol") i escollir el tipus de lletra a l'apartat "Aparença i temes -> Lletres". Segurament serà això, però digues-nos si t'ha funcionat o no.

P.D.: Potser et caldrà instal·lar el paquet "kcontrol" des del synaptic, perquè en tenir l'escriptori gnome no crec que el tinguis instal·lat per omissió.

---

### Post by ernestux on 2007-12-22
> **orestesmas said:**
> 
P.D.: Potser et caldrà instal·lar el paquet "kcontrol" des del synaptic, perquè en tenir l'escriptori gnome no crec que el tinguis instal·lat per omissió.
No tinc instal·lat el "kcontrol" he vist.
Ara he vist que les aplicacions es veien normals, de totes formes.
Provaré d'instal·lar-lo demà, ara no puc. Però -es clar- tampoc el tinc com a usuari inicial i no em dóna problemes.

Gràcies

---

### Post by CarlesOriol on 2007-12-23
Per tal d'usar aplicacions de kde en gnome es preferible que insta&#320;lis el kubuntu-desktop ja que et configura un munt d'aspectes d'aquest escriptori (el teclat entre altres). 

També és important d'entrar com a mínim un cop en kde en l'usuari que vas a usar els programes per tal de finalitzar les personalitzacions.

---

### Post by ernestux on 2007-12-24
> **ernestux said:**
> No tinc instal·lat el "kcontrol" he vist.
Gràcies
Vaig instal·lar el kcontrol i  seguia malament la configuració del khangman , amb lletres enormes. He fet al terminal "sudo kcontrol" i també es veia gran, i en l'aparença posava "normal".
Després he tingut problemes amb el so (no so) , que he atribuit al kcontrol. L'he desinstal·lat amb synaptic i el so ha tornat.

El kubuntu-desktop ocupa 120 MB ! (amb programes que no m'interessen) i per contra he instal·lat el kde-core . Les darreres vegades la usuària segueix tenint problemes amb aplicacions kde.
He creat un altre usuari i de moment sempre corren bé les aplicacions kde en gnome. O sigui, misteri !

Gràcies

---

### Post by CarlesOriol on 2007-12-25
El sudo kde sols et configura l'entorn de l'usuari root.

Si no tens res important sempre et pots carregar la carpeta /home/usuari/.kde

És probable que el kde tingui configurada la pantalla a un nombre de dpi (punts per polzada) diferent al del gnome. La configuració predeterminada d'aquest és de 75 i la del gnome de 96 per tant la conversió de mida de lletra a pixels de pantalla seria errònia.

En qualsevol cas et segueixo recomanant si pots que insta&#320;lis el kubuntu-desktop ja que realitza un munt de feines que el sol kde-core no fa.

---

### Post by ernestux on 2007-12-26
> **CarlesOriol said:**
>  ...  que insta&#320;lis el kubuntu-desktop ja que realitza un munt de feines que el sol kde-core no fa.

Amb el kde-core també m'ha fallat algun cop l'aplicació de kde en gnome.
Finalment he fet cas al Carles Oriol i he instal·lat el kubuntu-desktop  i de moment des d'ahir no m'ha fallat la configuració de les aplicacions kde en cap usuari.
Tin un problema però: Vull marcar en la finestra d'entrada d'ubuntu ,  kde en opcions    i em surten les lletres enormes i en marcar-ho segueix sortint entorn Gnome .

Gràcies

---

### Post by CarlesOriol on 2007-12-26
Quin gestor d'entrada has deixat configurat gdm o kdm?

---

### Post by ernestux on 2007-12-26
En instal·lar els paquets del kubuntu-desktop m'ho va preguntar: vaig dir **gdm**

---

### Post by CarlesOriol on 2007-12-27
Prova a :

sistema > administració > Finestra d'entrada > Seguretat > Configura el servidor X > Ordre

Canvies

```
/usr/bin/X -br -audit 0 
```

per 

```
/usr/bin/X -br -audit 0  -br -dpi 96 -audit 0 
```

a veure si va :-)

---

### Post by ernestux on 2007-12-27
Hola,
Seguint les indicacions d'en Carles Oriol tot ha anat perfecte: ja tinc opcions de quin escriptori triar quan engego ubuntu. De moment tot funciona. 
Gràcies Carles, especialment. Que els reis -d'orient- t'ho valorin !

---

