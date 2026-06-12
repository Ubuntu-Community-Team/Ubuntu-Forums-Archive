---
title: "Ubuntu 8.10 worked, now it doesn't"
date: 2009-05-22
forum: General Help
---

### Post by gasto on 2009-05-22
OK last year, I tried to install and make Ubuntu work on my PC, but I did not manage to install the Nvidia driver for the GeForce 6200 it has on the AGP slot.

So all of the sudden,after leaving Windows XP uploading some files at night, I wake up to find out that Ubuntu was working on my machine, how... I don't know, some benign hacker I guess.

My resolution was at 1024x 768y and it all worked properly, and at the correct resolution, using the recommended driver (as shown on the driver app).

But when I restarted Ubuntu, my machine won't show video, just like it did before the solution magically appeared. I am thinking it could be one of the dozen of updates made.

Any solutions would be really appreciated.

---

### Post by gasto on 2009-05-24
how do I get output from xorg/config ?

---

### Post by Super TWiT on 2009-05-24
I am not sure what happened, or how to fix this problem, but I would recommend downloading a newer version of Ubuntu and trying the install again. Hardware detection is always evolving.

---

### Post by DLG102282 on 2009-05-24
```
nano /etc/X11/xorg.conf
```

---

