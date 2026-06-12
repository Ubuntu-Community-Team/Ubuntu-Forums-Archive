---
title: "vino is broken"
date: 2009-04-30
forum: Desktop Environments
---

### Post by zebul on 2009-04-30
hi.
i just upgraded a ubuntu **8.04** to a **9.04**. i am happy as it seems the driver for my usb wifi key are better and i can use it at full speed of my connection. **BUT**

now i have big problem when i try to control this pc #1 from another one on the LAN. i use *vinagre* and i **can move the *mouse* but the click does nothing** and **the *keyboard*** **does nothing too**. i try to access it from a archlinux 32 bit pc#2 with *gnome 2.26.1* and **vinagre 2.26.1** (it's the same if i try from ubuntu 9.04 on the pc #2)
and it is horribly slow...

what's strange is that i can control the archlinux box (pc#2) from ubuntu 9.04(pc#1). 

i tried to use ethernet cable to check if the modem-router is not at fault (because it fails to broadcast properly avahi packet). but the problem is still the same with cable

i tried to boot the same pc#1 with a livecd of ubuntu 8.04 and it works. from my archlinux pc#2 vinagre 2.26.1. it works even if it is slow while i am on a lan and it should be fast almost instantsly. it feels slughish and poor with vinagre and vino. with vinagre and some vnc soft on windows it is better.

so something is wrong with **vino in ubuntu 9.04**. it's an upgrade problem ? the configuration of the previous vino in ubuntu 8.04. where is the configuration of vino so i can erase it and try

i need help because i can't find where this strange bug come from

also what happened to the advanced tab of Options -> Remote desktop to change port or hide background while connected ?

**Edit**
i tried with a new user and its the same.
so that's a bug in vino or what ? i am the only one ?

**Another Edit:**
if i run ubuntu 9.04 on pc#2, then i **can't either control it from pc#1 from ubuntu 9.04** because i don't have any problem with archlinux's vino version

so something is definetivly wrong with vino in ubuntu 9.04
a problem of permission ?

---

### Post by zebul on 2009-04-30
yeah that's definitvly a bug
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/350327](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/350327)

---

### Post by bc90021 on 2009-05-05
I am having the same issue.  It's the exact same behaviour as in the linked bug report above.

---

### Post by obryantr on 2009-05-11
Same problem. Any solution out there. When I look at configuration panel in remote desktop panel it states users can connect to localhost rather than the usual vinagre foobar:5900.  Help

---

### Post by satchm0h on 2009-09-17
Any workaround for this issue? Anyone had success w/ another VNC server on 4.09?

---

