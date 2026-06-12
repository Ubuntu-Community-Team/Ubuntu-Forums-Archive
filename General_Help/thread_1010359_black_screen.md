---
title: "black screen"
date: 2008-12-13
forum: General Help
---

### Post by Howitzer777 on 2008-12-13
When the ubuntu loading bar is done it goes into a black screen and nothing happens-or the screen blinks a few times. need help.I don't want links to other threads. I want the answer.

intel core 2 duo
ati raedon hd 2600 xt

also, i'm pretty sure its not my monitor cause it worked with previous ubuntu releases....its just a dell flat screen. i have a custom computer not a name brand

---

### Post by jbrown96 on 2008-12-13
What graphics drivers do you have installed? What version?

---

### Post by albinootje on 2008-12-13
It worked in Hardy and not in Intrepid ?

You can install with the alternate installation cdrom, and then manually configure xorg with dpkg-reconfigure -plow xserver-xorg (afair).

You can also boot from the Hardy installation cdrom, and then save the /etc/X11/xorg.conf somewhere, to using it as base for Intrepid.

---

