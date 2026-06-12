---
title: "Changing the quit menu"
date: 2006-07-05
forum: Desktop Environments
---

### Post by mrk112 on 2006-07-05
Hi,

Is it possible to remove the hibernate option from the quit menu? I've noticed that when you run the live CD it isn't there so it has to be possible..

The reason I ask is because when attempting to hibernate on my PC it completely messes up and I'm lucky if I can boot up again. But my partner also uses my PC and she has a habit of clicking things she shouldn't..

Many thanks..

---

### Post by reacocard on 2006-07-05
no idea for how to remove options, but i may have a solution for your hibernation trouble. use suspend2: [http://dagobah.ucc.asn.au/dapper-kernels/](http://dagobah.ucc.asn.au/dapper-kernels/)
hibernation didn't work for me either, but suspend2 works perfectly. (NOTE: suspend2 does not override the log out menu. you have to run it with sudo hibernate)

---

### Post by 23meg on 2006-07-05
In gconf-editor untick this key: /apps/gnome-power-manager/can_hibernate

---

### Post by reacocard on 2006-07-05
awesome 23meg. works wonderfully. any ideas on how to add/change an entry (so i can point hibernate to suspend2)

---

