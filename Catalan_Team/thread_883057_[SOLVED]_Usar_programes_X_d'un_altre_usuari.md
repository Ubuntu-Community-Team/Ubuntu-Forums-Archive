---
title: "[SOLVED] Usar programes X d'un altre usuari"
date: 2008-08-07
forum: Catalan Team
---

### Post by CarlesOriol on 2008-08-07
Hola colla.

Tinc dos usuaris: 1- **carles**, 2- **coriol** 

inicio la sessió **carles**, però voldria usar programes en X inpersonant l'altre usuari.

He provat un **ssh coriol@127.0.0.1 -X** i després executar el programa, però crec que hi deu haver alguna forma millor.

Alguna idea?

---

### Post by papapep on 2008-08-07
I un:

> gksu -u coriol --su-mode gedit

et serviria?

---

### Post by orestesmas on 2008-08-07
I un ```
xhost +
``` per permetre que altres usuaris puguin usar el teu DISPLAY?

---

### Post by CarlesOriol on 2008-08-08
Ok. Combinant els 2 funciona.

Vaig a provar de limitar l'àmbit de l'xhost +

Gràcies

---

### Post by CarlesOriol on 2008-08-08
xhost +SI:localuser:coriol

Compte!!! Hi ha un error en la documentació de l'xhost.

---

