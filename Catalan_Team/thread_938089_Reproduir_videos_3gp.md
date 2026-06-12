---
title: "Reproduir videos 3gp"
date: 2008-10-04
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-10-04
Bones.
Tinc uns vídeos *.3gp baixats d'un mòbil.
Els puc reproduir, però no s'escolta el so.
Algú te la certesa d'algun programa per reproduir-los be?
Consti que abans d'aquest post he fet un fart de "googlejar", però res
m'ha funcionat :( 
Salut!

---

### Post by lluisanunez on 2008-10-04
Prova ffmpeg
```
ffmpeg -i video.3gp -b 250 -s 160×120 -r 15 -f avi -an video.avi
```

---

### Post by Miquel Ubuntero on 2008-10-05
Hola.
No hem funciona. Diu "Incorrect frame size".
Gracies LLuisa.

---

### Post by CarlesOriol on 2008-10-05
Mmm.. crec recordar que pel format 3gp cal una compilació especial del ffmpeg. 

Crec que la de medibuntu ho fa.

(Una altra opció és penjar el video al youtube :-D.... no riguis... que funciona!)

---

