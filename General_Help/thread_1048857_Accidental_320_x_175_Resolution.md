---
title: "Accidental 320 x 175 Resolution"
date: 2009-01-23
forum: General Help
---

### Post by kortez on 2009-01-23
I accidentally set my screen resolution to 320 x 175 using Monitor Resolution Settings. I thought I would see what it would look like for something to do but now I cannot change it back to 1024 x 768. This is because the resolution is so low that I cannot even make the mouse go to the part of the window that allows you to change the resolution in the box or even see that part of the window even when the window is at the top of the screen. I thought that doing sudo dpkg-reconfigure -phigh xserver-xorg in the failsafe terminal would do the trick and fix it but it didn't. Is there some command I should do? How do I get back my 1024 x 768 resolution ?!?!

---

### Post by IncadudeF on 2009-01-24
try:

sudo dpkg-reconfigure xserver-xorg

---

### Post by mcduck on 2009-01-24
> **kortez said:**
> now I cannot change it back to 1024 x 768. This is because the resolution is so low that I cannot even make the mouse go to the part of the window that allows you to change the resolution in the box or even see that part of the window even when the window is at the top of the screen.

When you hold down the Alt key you can drag windows around from any point in the window (instead of just the titlebar). This should allow you to move the window around so you can access all settings.

(Alt+left button is move, Alt+middle button resizes window)

---

### Post by gjoellee on 2009-01-24
Try to run xfix. Take a look here for how its done: [http://www.kshoster.net/content/howto-run-xfix](http://www.kshoster.net/content/howto-run-xfix)

If Xfix does not work let's manually configure Xorg. Please post the output of this command: ```
cat /etc/X11/xorg.conf
``` NOTE: You don't have to do that if xfix works.

---

### Post by kortez on 2009-01-24
Thank you mcduck! That helped a lot. LOL, all of our avatars are penguins.

---

### Post by gjoellee on 2009-01-24
> **kortez said:**
> all of our avatars are penguins.

Because we love Linux :D

---

