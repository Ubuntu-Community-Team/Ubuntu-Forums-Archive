---
title: "[SOLVED] Fer un PDFa partir d'una URL"
date: 2007-12-30
forum: Catalan Team
---

### Post by prostata on 2007-12-30
Bon dia i bon any 2008 a t@ts!!!!!!

Doncs això, vull fer una arxiu PDF a partir d'una URL, per exemple aquesta, ¿com puc fer-lo?, des de windows amb acrobat professional, si que en sé però des de ubuntu no en tinc ni idea..gràcies

Salut

---

### Post by papapep on 2007-12-30
Només et cal instal·lar el paquet cups-pdf:

```
sudo aptitude install cups-pdf
```

Seguidament, vas a configuració d'impressores i en crees una que utilitzi el controlador postcrip i que vols instal·lar la "pdf virtual printer". 
A partir d'aquí, qualsevol cosa que sigui imprimible la podràs enviar a aquesta impressora com si de qualsevol altra es tractés i es generarà un pdf.

---

### Post by prostata on 2007-12-31
> **papapep said:**
> Només et cal instal·lar el paquet cups-pdf:

```
sudo aptitude install cups-pdf
```

Seguidament, vas a configuració d'impressores i en crees una que utilitzi el controlador postcrip i que vols instal·lar la "pdf virtual printer". 
A partir d'aquí, qualsevol cosa que sigui imprimible la podràs enviar a aquesta impressora com si de qualsevol altra es tractés i es generarà un pdf.

A veure, aniré a pams:

Ja tinc una impressora cups-pdf
mirant les propietats d'aquesta impressora no hi ha cap controlador postcrip.

Si vaig a crear una nova impressora, veig que aquesta a de estar asignada a una impressora (¿fìsica?), com a pas previ, i després on és el controlador postcrip que no el trobo?? he fet una busqueda i no el veig per en lloc...

gràcies papapep...

Ja he trobat la solució.....gràcies

---

### Post by SiscoGarcia on 2008-01-01
Prostata, dius que ja has trobat la solució. Per què no ens la descrius i així ens servirà a la resta?:)

---

### Post by prostata on 2008-01-02
Si, tens raó Sisco, la solució és la que deia en papapep, malgrat que jo ara mateix tinc certs problemes, però va per on diu el company....disculpa el "lapssos".

Salutacions

---

