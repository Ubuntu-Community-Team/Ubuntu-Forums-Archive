---
title: "Warcraft 3 crashing/freezing"
date: 2006-06-12
forum: Gaming &amp; Leisure
---

### Post by nephesh on 2006-06-12
I'm running on Ubuntu 6.06 with a Radeon 9800 pro (128mb) on an Opteron machine (which means I'm running the (linux-k7 kernel).  My system is rock solid until I try to play Warcraft III in Wine.  I can play for quite a while and all will seem fine, but then randomly, it will freeze up or just reboot.  I'm not really sure how to go about trouble shooting this.

My fglrxinfo shows the proper info

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

so I'm not really sure why it's being so unstable.  Has anyone had any experience with this problem before?

EDIT:  I am running wine 9.15 from the wine repo

---

### Post by d-hunter on 2006-06-12
Hava you tried to run game with -opengl -parament?
wine war3.exe -opengl

Works fine with me (Radeon 9600).

---

### Post by nephesh on 2006-06-12
Yes I have tried that and it freezes every time.

---

### Post by nephesh on 2006-06-13
Well I have discovered what the problem was.  It wasn't Wine, it wasn't ATI drivers, it was the agp on my board.  I changed it to only use 4x agp in the bios and now I have rock solid stability.

---

