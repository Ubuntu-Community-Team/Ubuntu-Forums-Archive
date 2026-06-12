---
title: "El Firefox es mor"
date: 2008-05-10
forum: Catalan Team
---

### Post by LitusMayol on 2008-05-10
Bones!

Com va dir algú de per aquí: sóc la persona més desesperada d'aquesta banda del Besòs. ehhe


A veure. Mireu:

```
litus@mayolets:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault
litus@mayolets:~$ firefox-2
Segmentation fault
```

Els Firefox de tan en tan em peten (aquest intèrval de temps equival a uns 5-1o minuts). Em preocupa i és molest treballar-hi. Quan ho he probat amb consola m'ha sortit el que teniu a dalt. Algú se li acut re? 


Entre això i l'HDD estic que no m'ho crec... :'(

---

### Post by pespin on 2008-05-10
És força estrany, aquests errors són de programació. Tens algun addon instal·lat que no vingui per defecte? Estàs fent cap cosa concreta quan et peta el programa?

---

### Post by CarlesOriol on 2008-05-11
Prova de canviar de nom la carpeta oculta .mozilla (a la teva carpeta home a .mozillavell per exemple) i així reinicialitzar la teva configuració (pluggins i tot nou) a veure que passa. Si peta igualment restaura la carpeta tornant-la al nomoriginal.

---

