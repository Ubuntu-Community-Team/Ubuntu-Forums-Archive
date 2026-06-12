---
title: "Kdenlive, no apareix icona ni el veig enlloc"
date: 2008-04-29
forum: Catalan Team
---

### Post by bikerbaixcamp on 2008-04-29
Hola companys!

M'acabo d'instal·lar la versió 8.04 :)

Doncs bé, he anat al Synaptic i he instal·lat els dos paquets del Kdenlive (per fer vídeos). Doncs bé, no m'apareix ni al lloc d'aplicacions; ni buscant al Menú Principal no fos cas que s'hagués de seleccionar la icona.
Vaja, que deu estar descarregat, però no sé trobar-lo ni sé posar cap icona òbviament sinó sé on és.

Merci!

---

### Post by kukat on 2008-04-30
Escriu a la consola kdenlive, i ja et funcionarà. 

Pots crear també un llançador clicant amb el botó dret sobre el menú (en lo de Aplicacions, Llocs, Sistema) i dient-li "Edita els Menus", "Element Nou", i posant com a ordre kdenlive, igual que abans a la consola (en minuscules)

I la icona....no se. Pots clicar sobre la foto del llançador per canviar-la, però jo no se on està tampoc. Podem buscar-la per internet....

Però la veritat, a mi m'ha passat el mateix, no hem surt el Kdenlive:)

---

### Post by bikerbaixcamp on 2008-04-30
Fet! Tot perfecte, així ja ho sabré per altres programes.

El que passa es que de cada 7 cops de 10 que clico doncs peta i em fa sortir de la sessió :(

No ho sé a que es deu...

Salut!

---

### Post by orestesmas on 2008-04-30
> **kukat said:**
> 

I la icona....no se. Pots clicar sobre la foto del llançador per canviar-la, però jo no se on està tampoc. Podem buscar-la per internet....


No cal: obriu una consola i feu:

```

locate kdenlive

```

Veureu que surten moltes línies, i fixant-vos en les que acaben en ".PNG" es veu que pots trobar una icona a (per exemple) /usr/share/icons/hicolor/64x64/apps/kdenlive.png

---

### Post by RainCT on 2008-04-30
> **orestesmas said:**
> No cal: obriu una consola i feu: locate kdenlive

Però per a això cal haver creat la base de dades del locate. Una altre possibilitat és: **dpkg -L kdenlive kdenlive-data** (això mostrarà tots els fitxers que el paquet kdenlive ha insta&#320;lat, entre els quals hauria d'estar el PNG). Si fas **dpkg -L kdenlive kdenlive-data | grep -i png** només et mostrarà les entrades que continguin "png" (això del grep també ho pots fer amb el que t'ha proposat l'Orestes; quedaria: *locate kdenlive | grep -i png*).

De totes formes, per a futurs casos, primer de tot pots comprovar a veure si està a /usr/share/pixmaps, que és on haurien d'estar totes les icones.

---

### Post by bikerbaixcamp on 2008-04-30
El tema de la icona cap problema. Quan he fet crear llençadora i he posat kdenlive doncs s'ha posat una icona automàticament. Ja que suposo que els paquets del programa ja fa que quan sigui una ordre kdenlive surti l'icona.

D'altra banda, el que no s'acaba d'arreglar és això, que al pitjar per executar el programa a vegades es queda la pantalla tota negra uns segons i em surt de l'usuari, i es posa la pantalla d'inici on he de posar usuari i contrasenya i per tant es perd tot el que s'estava fent.

:wink:

---

### Post by orestesmas on 2008-04-30
Això que et passa és que et peten les "X". Probablement la causa és que tens activats els efectes d'escriptori, i que el kdenlive no s'entén bé amb ells. Prova de desactivar-los i a veure si et peta tant (jo no els tinc activats i et puc assegurar que no em peta)

---

### Post by Aljullu on 2008-04-30
Per desgràcia el Kdenlive és força inestable. De moment estant fent una [nova versió]("http://www.kdenlive.org/news.php") que [pinta bé]("http://www.kdenlive.org/images/kdenlive-kde4full.png").

A més a més, a mi no m'extreu bé.[-(

---

### Post by bikerbaixcamp on 2008-04-30
Fet, doncs deu ser això.

Amb les actualitzacions es millorarà?

Salut!

---

