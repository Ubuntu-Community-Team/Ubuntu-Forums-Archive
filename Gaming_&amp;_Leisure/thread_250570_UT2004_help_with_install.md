---
title: "UT2004 help with install"
date: 2006-09-04
forum: Gaming &amp; Leisure
---

### Post by Clockwise on 2006-09-04
When I was installing UT2004 Linux demo I did all the steps and then when I got to this part it was trouble. /usr/local/games/ut2004demo I have a x86 machine though Operating System: Debian GNU/Linux

Once I hitted ok it said No write permission to /usr/local/games. What do I put there?:-k

---

### Post by aX- on 2006-09-04
I had the same problem when I installed ut2k4.

I just ended up installing it here: /home/username/games/ut2004/

---

### Post by fatsheep on 2006-09-04
You need to run the installation script with root permissions of just install it in your home/user directory.

To run with root permissions, open up a terminal.  Type:

> 
sudo


Now drag you installation script into the terminal window right after sudo.  Press enter.  Hope this helps. :KS

---

### Post by artinla on 2006-09-04
OR you could just type **sudo chmod -R 777 /usr/local/games**

---

### Post by artinla on 2006-09-04
LOL you beat me to it fatsheep.

---

