---
title: "Red Alert 2 Issue (Not about installing or running slow)"
date: 2006-08-27
forum: Gaming &amp; Leisure
---

### Post by amgeex on 2006-08-27
Ok, I've got my Red Alert 2 game installed, it runs at proper speed. The problem is, everytime I start the game, it thinks it's the first time, so it always shows the movie about the president and stuff, and I can't cancel it, no matter what I type or click. 

Anyone got any ideas? I'm thinking somethings get added to the Ra2.ini file, so I went ahead and tried to modify it with gedit, but I couldn't because gedit told me it was on a read-only hard drive. Is this normal?

Thanks! :-k

---

### Post by amgeex on 2006-08-27
Exactly what I thought! This line gets added to the ra2.ini file:

[Intro]

Play=no

Just add it before this part: [SerialDefaults] 

You're good to go! :D

---

### Post by favad on 2006-09-05
Sir may I know how did you manage to install it and also at normal speed, as as yet I havent read a post saying this. I'd be glad if you could post the correct working link, or the method itself.

Thanks!

favad

---

