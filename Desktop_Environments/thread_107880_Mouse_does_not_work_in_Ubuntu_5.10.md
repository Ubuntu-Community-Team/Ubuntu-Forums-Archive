---
title: "Mouse does not work in Ubuntu 5.10"
date: 2005-12-24
forum: Desktop Environments
---

### Post by murthy on 2005-12-24
I have just tried Ubuntu 5.10, the installation goes on smoothly, the mouse pointer appears on the screen but does not move.  Similar problem in Live CD.  By trying several key combinations, (Alt+F2) I got the terminal but do not know how to solve the problem.  In the warty warthog version also I had the same problem with the mouse.  I think it needs to be configured properly, HOW?
Pentium II 300MHz, 128 MB, 20GB, Trident AGP 4MB, Logitech scroll mouse - serial. Please Help.

---

### Post by cbudden on 2005-12-24
Is it a usb/ps2 mouse or something more exotic?

---

### Post by murthy on 2005-12-24
[QUOTE=cbudden]Is it a usb/ps2 mouse or something more exotic?[/QUOTE]
No, nothing exotic - serial mouse.  Works in Redhat 9 if selected as Microsoft intellimouse serial.  How to change mouse configuration in Ubuntu?

---

### Post by ZedLord on 2005-12-24
See if This Works
[https://wiki.ubuntu.com/SerialMouseHowto](https://wiki.ubuntu.com/SerialMouseHowto)

[SIZE="1"](P.S-ZedLord = Subbu:KS )[/SIZE]

---

### Post by murthy on 2005-12-27
Thanks.  I also found out about the howto and edited the xconfig file.  Now the mouse is working, but the scroll function does not work.  Probably changing the option to "Microsoft Intellimouse"  may solve the problem.  I will try.  Also sound is not working.  (creative Vibra sound card).  I may have to mess around a lot more to get ubuntu working properly!!

---

### Post by murthy on 2005-12-29
logitech scroll mouse is now working after I edited the /etc/X11/xorg.conf file by commenting out emulate 3 button andchanging the  protocol to  "intellimouse" from "Microsoft".  Now the scroll wheel is working.  Details in the following link:
[http://www.icewalkers.com/Linux/Howto/3-Button-Mouse-7.html](http://www.icewalkers.com/Linux/Howto/3-Button-Mouse-7.html)
However sound is not working.  (Creative Vibra pci sound card, works in RedHat 9)

---

