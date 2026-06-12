---
title: "[SOLVED] xip Ralink i Hardy"
date: 2008-06-04
forum: Catalan Team
---

### Post by climent on 2008-06-04
Salut, companyes i companys.
Tinc un xip Ralink per la wifi, el "famós" rt73 que cada cop que actualitzo el Hardy amb arxius importants he de tornar a instal·lar. Això no m'amoïna; el cas és que googlejant per trobar el procés d'instal·lació he llegit que a Gutsy ja estava per defecte el driver rt73 i no el rt73usb "dolent". Podria algú dir-me si a Hardy ve instal·lat?

---

### Post by papapep on 2008-06-04
Sembla ser, hi ha uns quants articles al respecte a internet, que sí que hauria de funcionar amb Hardy.

El que comenten és que caldria, si és el cas, modificar el fitxer */etc/modprobe.d/blacklist* a fi de modificar la línia:

```
r73usb
```

i deixar-la:

```
r73
```

Evidentment, si no tens això dins el fitxer, doncs ni cas.

---

### Post by climent on 2008-06-06
Doncs no, no el tinc a la llista. Com que, de moment vaig tirant, continuaré així. Gràcies

---

