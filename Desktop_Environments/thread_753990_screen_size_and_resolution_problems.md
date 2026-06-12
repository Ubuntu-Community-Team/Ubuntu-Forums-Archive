---
title: "screen size and resolution problems"
date: 2008-04-13
forum: Desktop Environments
---

### Post by napolean9 on 2008-04-13
hi recently i added the game frets on fire because it looked like a fun game. i installed it and played the tutorial for a bit. then i quit the game, and for some reason, my resolution and screen size was totally off... at least i think that is what happened. basically the screen had liked zoomed up a LOT and i could only see like a 1/4 of the screen at a time, i had to mouse around to see the whole screen. so i tried to fix my resolution and screen size but i can't seem to find my default settings. how can i get back my default settings?

---

### Post by tzulberti on 2008-04-14
Try writing "sudo dpkg-reconfigure xserver-xorg" in console, and then restart. It should ask you about the resolution (and many other things). Then restart xorg using "sudo /etc/init.d/gdm restart"

---

### Post by paul101 on 2008-04-14
is it the "enhanced desktop zoom" plugin in compiz??

try pressing super + 1 :)

---

