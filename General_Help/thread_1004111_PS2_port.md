---
title: "PS/2 port"
date: 2008-12-06
forum: General Help
---

### Post by Graf555 on 2008-12-06
Hi, all!)

At this moment I'm working without a mouse a two days, because:
1) My previous USB-mouse was bad, so ...has been broken, by myself)
2) My new mouse has a PS/2 port, but the only one motherboard's PS/2 is for keyboard. (It's free, my keyboard is on usb)
And I want to link up my mouse with this keyboard port. I've tried to do

ln -s /dev/psaux /dev/input/mice

and in xorg.conf mouse's section was written the following string:
[Inputdevice]
  ...
  Option "Protocol" "PS/2"

but it hasn't an effect on my mouse

In /dev/input also are "mouse0" and "mouse1" files, but with them it doesn't work, too. 
I'll appreciate for any help!)

---

### Post by eBoxNet on 2008-12-06
hope that helps
[http://ubuntuforums.org/showthread.php?t=179818](http://ubuntuforums.org/showthread.php?t=179818)

---

### Post by Graf555 on 2008-12-07
Thanks, there I've found other links, that helped me to know something more about this topic) But it seems, I have to go to buy a new device >_<

---

