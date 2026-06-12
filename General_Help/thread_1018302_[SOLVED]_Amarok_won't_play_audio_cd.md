---
title: "[SOLVED] Amarok won't play audio cd"
date: 2008-12-22
forum: General Help
---

### Post by paydaydaddy on 2008-12-22
Using kubuntu 8.04. Tried to listen to an audio cd using Amarok. No luck. More than likely operator error, but if I could get a little help making this work, it would be greatly appreciated.

---

### Post by 2hot6ft2 on 2008-12-22
will it work in another app like rhythmbox?

---

### Post by paydaydaddy on 2008-12-22
Can play with Kaffeine

---

### Post by paydaydaddy on 2008-12-22
Can Amarok be used as a player? When I load an audio cd in the cdrom/burner I get a popup applet that gives me a choice to play cd with Amarok, but so far I have not figured out how to get it to play with Amarok. I cannot get Amarok to recognize the cd. I am sure that I am overlooking something simple.

---

### Post by SlidingHorn on 2008-12-22
probably is, but just to be sure, do you have the device set to /dev/cdrom   ?

---

### Post by paydaydaddy on 2008-12-22
Just exactly how do you set the device to cdrom?

---

### Post by SlidingHorn on 2008-12-22
Under Settings, check out the Engine tab and see what the default device is (running off old info, so it may not be exact)

try running "cat /etc/fstab" in your terminal and use whatever is listed as your cd-rom drive is the default

---

### Post by paydaydaddy on 2008-12-22
:guitar:That made it happen. Really not a big deal, but it was one of those things that drives you crazy. thanks

---

### Post by Ganton on 2011-04-18
> **paydaydaddy said:**
> Can play with Kaffeine
YES! Installing Kaffeine added a "Play audio CD with Kaffeine" and it dealt with it.

Thank you!

---

