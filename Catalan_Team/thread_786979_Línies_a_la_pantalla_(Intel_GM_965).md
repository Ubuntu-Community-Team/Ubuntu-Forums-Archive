---
title: "Línies a la pantalla (Intel GM 965)"
date: 2008-05-08
forum: Catalan Team
---

### Post by menut on 2008-05-08
I així m'he trobat el portàtil aquesta tarda: un munt de línies horitzontals a la pantalla.
He fet un Ctrl+Atl+Backspace i tot igual. He fet una captura de pantalla, però me les fa correctes (sense línies).
He reiniciat vàries vegades, i ja no sé que fer.

Sortida del lspci:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

---

### Post by elbuit on 2008-05-09
Una pregunta, si li desactives els efectes visuals(compiz), continua fent-ho?
Si reprodueixes un avi, també ho fa?

---

### Post by papapep on 2008-05-09
Pel que comentes Menut, de que fent un volcat de pantalla surt bé, pinta a problema de ferro del monitor...
Jo provaria amb un altre monitor per verificar que el senyal de la placa surt bé.

---

### Post by CarlesOriol on 2008-05-10
> **papapep said:**
> Pel que comentes Menut, de que fent un volcat de pantalla surt bé, pinta a problema de ferro del monitor...
Jo provaria amb un altre monitor per verificar que el senyal de la placa surt bé.

Al monitor ??!!??!! ni de conya. És configuració de gràfica. Ja sigui un bug al controlador o una configuració d'aquest que dona problemes. I si de cas es podria haver trencat la gràfica... però m'extranya.

---

### Post by menut on 2008-05-12
Problema sol·lucionat.
He estat provant amb monitors secundaris, ampliant l'escriptori i resulta que en reiniciar amb 2 monitors connectats (principial i extern) han marxat les línies.

Després, al desconnectar el monitor secundari, tot ha seguit correctament.

---

