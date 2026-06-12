---
title: "How to EASY reconfigure Xserver after changing video card?"
date: 2006-07-09
forum: Desktop Environments
---

### Post by DoktorNo on 2006-07-09
Hello,

I am going to upgrade from my old video card GeForce2 to Readon 9250. As everyone knows, the xserver hangs after so significant change in hardware. I heard, that doing this in ttype:
```
sudo dpkg-reconfigure xserver-xorg
```
is OK, but I also heard, that 
```
X -configure
```
is also good.

What to choose? I loking for the easest way.

---

### Post by reacocard on 2006-07-09
first one. nice frame based interface, step you through the process easily.

---

### Post by DoktorNo on 2006-07-09
OK, but what questions are asked by this script? Video card type, and what else?

Sorry, but I must prepare guide for noob user, and I must know in advance what he should do. :)

---

### Post by taurus on 2006-07-09
"sudo dpkg-reconfigure xserver-xorg" will ask you about your video card, screen resolution, etc. Just follow the instructions on the screen because it's as easy as 1-2-3!!!

---

