---
title: "Monitor problem?"
date: 2008-12-02
forum: Desktop Environments
---

### Post by Oneofchaos on 2008-12-02
Hey all, I'm an ubuntu newb, and after finally somehow reformatting my lenovo thinkpad t61p's harddrive, I got XP working and linux was next.  When I installed linux it needed Nvidea drivers and now I can't boot up, I get a blank screen.  Any ideas of where to start?

---

### Post by Oneofchaos on 2008-12-03
Please help me

---

### Post by Zorael on 2008-12-03
Have you tried booting up into recovery mode and picking 'fix X'? I think that should have the appropriate effect.

Else pick 'root shell' and enter the following. (Omit the hashmarks; that's just syntax convention to show it should be entered in a terminal as root - which you are, in recovery mode.)
```
# cd /etc/X11
# mv xorg.conf xorg.backup0812
# dpkg-reconfigure -phigh xserver-xorg
# exit
```
Then pick 'start x' or whatever the entry is named, to try to start the graphical environment.

---

### Post by whansen02 on 2008-12-03
> **Zorael said:**
> Have you tried booting up into recovery mode and picking 'fix X'? I think that should have the appropriate effect.

Else pick 'root shell' and enter the following. (Omit the hashmarks; that's just syntax convention to show it should be entered in a terminal as root - which you are, in recovery mode.)
```
# cd /etc/X11
# mv xorg.conf xorg.backup0812
# dpkg-reconfigure -phigh xserver-xorg
# exit
```
Then pick 'start x' or whatever the entry is named, to try to start the graphical environment.
I can't see why this wouldn't work **Oneofchaos**. Have you had success or what?

---

### Post by Oneofchaos on 2008-12-03
I downloaded nvidia drivers through the shell script on the nvidia site that requires you to shutdown your x server to install the drivers, and when it got done installing, all I get is a black screen. Its not frozen though because when I hit Ctrl-Alt-F2 I get a command prompt. I tried doing many things with xorg.conf, but to no avail, I even tried # dpkg-reconfigure -phigh xserver-xorg
 but it still doesn't work

---

### Post by Oneofchaos on 2008-12-04
Please help!

---

### Post by Oneofchaos on 2008-12-05
please?

---

### Post by Oneofchaos on 2008-12-05
still stuck here

---

### Post by Oneofchaos on 2008-12-06
please help

---

### Post by Oneofchaos on 2008-12-09
help please!

---

