---
title: "[SOLVED] Instal·lació del nucli 2.6.27.7 a la cabra intrèpida"
date: 2008-10-26
forum: Catalan Team
---

### Post by SiscoGarcia on 2008-10-26
Hola,

Ahir vaig actualitzar-me a la cabra intrèpida (8.10) i em va baixar el nucli 2.6.27.7 de linux (adjunto captura de synaptic), però no se'm va instal·lar (adjunto el fitxer menu.lst del grub). Per si de cas al synaptic he triat el nucli ja instal·lat i l'he reinstal·lat, però tampoc no surt al menú del grub. De ser-hi hi és perquè apareix a la carpeta /boot (també adjunto captura). Suposo que no es va instal·lar perquè arribat el moment vaig triar l'opció de mantenir el que hi havia (amb l'actualització a la 8.04 no ho vaig fer i vaig tenir problemes). La cosa és que m'agradaria actualitzar el nucli i no sé què puc fer.

Alguna idea?

Merci.

---

### Post by papapep on 2008-10-26
Si afegeixes aquestes línies al teu menu.lst, t'hauria d'arrencar (sempre que sigui el primer de tots) amb aquesta versió:

```
title		Ubuntu 8.10 amb el nucli 2.6.27-7
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=af58ba2d-7ed4-407b-8d5b-b5dca110bd70 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet
```

---

### Post by SiscoGarcia on 2008-10-26
Gràcies papapep. Hi havia pensat però em feia por.

Suposo que per les modalitats de recuperació (recovery mode) i prova de memòria (memtest) serà equivalent, oi?

---

### Post by papapep on 2008-10-26
Exacte. Tot i que el memtest és únic, no n'hi ha pas un per a cada nucli.

---

### Post by SiscoGarcia on 2008-10-26
D'acord, moltíssimes gràcies ;)

---

