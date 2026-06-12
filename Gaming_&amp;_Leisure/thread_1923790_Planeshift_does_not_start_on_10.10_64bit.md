---
title: "Planeshift does not start on 10.10 64bit"
date: 2012-02-11
forum: Gaming &amp; Leisure
---

### Post by BcRich on 2012-02-11
Hi 
I just downloaded Planeshift from planeshift.it and went along with the installation, which seemed to go well. Chose not to install as root and using Gnome DM. The installed placed an icon on my desktop which when i clicked it launched the Planeshift startup screen. The launcher identified that there is a new version of Planeshift and asked me if I wanted to update my installation. I said yes, it subsequently downloaded more data roughly the same same as the original download totalling approx 1.5GB. It got to the end of the update process, Said "Done" "Success" updating linux client (or something to that effect) downloaded another file about 1MB or so then just exited. No error message or anything like that. Just disappeared. So I tried starting the launcher again from the installed desktop icon, and nothing. tried running pslaunch from terminal and I get

```
home/bcrich/software/games/PS/PlaneShift/pslaunch: line 5: home/bcrich/software/games/PS/PlaneShift/pslaunch.bin: Permission denied
/home/bcrich/software/games/PS/PlaneShift/pslaunch: line 5: exec: /home/bcrich/software/games/PS/PlaneShift/pslaunch.bin: cannot execute: Permission denied

```

tried running it with sudo (which should not be the case since i did not install it as root) and I get the same message

so I tried running psclient and I get 

```
Your configuration files are in... /home/bcrich/.PlaneShift
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  130 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x4200002
  Serial number of failed request:  118
  Current serial number in output stream:  122
AL lib: ALc.c:1879: exit(): closing 1 Device
```
Any help would be greatly appreciated aside from re-updating the game as i really don't want to have to do all of that downloading again.
thanks

Ubuntu studio 10.10 64bit
AMD 1075T
AMD 6850 1GB (Catalyst 11.5)
8GB RAM

---

### Post by Dlambert on 2012-02-11
I would re-install, I had similar problems with the game installing as root.

---

### Post by BcRich on 2012-02-11
Weird now it works, dunno what I did though :confused:

---

### Post by Dlambert on 2012-02-11
Haha, well hey, at least it works. :)

---

