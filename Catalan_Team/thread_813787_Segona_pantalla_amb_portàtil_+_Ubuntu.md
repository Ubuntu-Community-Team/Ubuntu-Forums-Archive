---
title: "Segona pantalla amb portàtil + Ubuntu"
date: 2008-05-31
forum: Catalan Team
---

### Post by lluisalguero on 2008-05-31
He connectat la sortida dvi del portàtil a la tele i estic mirant com puc fer servir la tele com a escriptori estés del principal.

Al ficar en marxa el pc, el logo i la barra de quan carrega si apareix, però despres ja no és veu res mes.

Amb el finestres em passava el mateix i ho he pogut solucionar, però a l'ubuntu fa estona que miro i rebusco i no trobo per on agafar-ho.

Si algú em pot guiar, gràcies,

Lluís

---

### Post by Frealof on 2008-06-09
Iep!

Molt bones, no sé si et servirà d'ajuda o no, però aquí va una idea ;)

Primer potser ajudaria saber quina gràfica tens, controlador... amb el què ens dius per aquí, poca cosa podem saber XD.

Jo en el meu cas tinc una nVidia Geforce 7300 GT, i el Driver que utilitzo es el propietari de la casa, instal·lat a través de l'ENVY... 

M'ho he estat mirant una mica, i Sistema/administració/nVidia X Server Settings hi ha una opció que hi posa X Server Display Configuration... a aquí pots afegir els monitors que et facin falta, o simplement posar-ho en "automàtic".

Espero que et serveixi d'alguna cosa :)

Salut!

---

### Post by lluisalguero on 2008-06-09
Tinc una GeForce Go 7600. I he fet això que m'has dit i les úniques opcions que em dona son 640x480 i 320x240, a totes llums insuficient.

---

### Post by papapep on 2008-06-09
Has provat amb l'[Envy]("http://www.albertomilone.com/envyngfaq.html#A")?

---

### Post by lluisalguero on 2008-06-09
> **papapep said:**
> Has provat amb l'[Envy]("http://www.albertomilone.com/envyngfaq.html#A")?

Tant aviat com pugui connectar el portàtil a la pantalla de la TV, ja us comentaré com m'anat...

---

### Post by CarlesOriol on 2008-06-09
No cal l'envy, de fet per una nvidia no cal mai.

Insta&#320;la el nvidia-settings.

Executa'l amb sudo si vols canvis permanents al xorg.conf

---

### Post by merril on 2009-02-14
tinc un problema semblant.
Al connectar el segon monitor, Ubuntu m'ha demanat que reiniciés, i al tornar a engegar, la barra de menús superior m'ha desaparegut i no puc accedir a cap menú amb el ratolí, bé, només puc accedir al menú de configuració de l'escriptori però no puc canviar la configuració de la pantalla en sí.


Algú em pot dir com puc accedir al terminal o als menús de configuració dels monitors **només amb el teclat**?

El meu equip es un portàtil de l'any de la Quica amb una tarja integrada, però no tinc ni idea de la configuració...:(
Moltes gracies i salutacions.

---

### Post by papapep on 2009-02-14
Hola Merril,

Obre un fil específic pel teu tema, si us plau.

I quan ho facis, ja hi pots enganxar el que et surti en fer:

```
lspci -v
```

al terminal que et sortirà en fer Ctrl+F1 (o Fn, sent n fins a 5), després d'identificar-te, clar.

Salutacions.

---

