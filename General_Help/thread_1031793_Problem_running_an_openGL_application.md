---
title: "Problem running an openGL application"
date: 2009-01-05
forum: General Help
---

### Post by julfi on 2009-01-05
Hi !

I tried to run an openGL application(MIT proto) [http://groups.csail.mit.edu/stpg/downloads.php]("http://groups.csail.mit.edu/stpg/downloads.php"), 
but I got this error:

```
freeglut (./proto):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  24
  Current serial number in output stream:  24

```

I have Intel Corporation 82852/855GM Integrated graphic card.
This application is working properly on openSuse 11.1

Thank you !
jani

---

### Post by julfi on 2009-01-07
I noticed that the problem is on Ubuntu, because on other distributions work fine. 

Does anybody have the same problem with some other openGL application ?

---

### Post by thedarkwinter on 2009-01-07
Hi 

Which graphics driver are you using?

I have a different Intel card, but your Device in /etc/X11/xorg.conf should look something like this (my openGL is fine)

```

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "Intel X3100"
        Busid           "PCI:0:2:0"
        Driver          "intel"
        Option          "DRI" "true"
        Option          "NoDDC"
        Screen  0
EndSection

```

typing 'glxgears' should pop up a little opengl app if its working, otherwise 'glxinfo' may provide some assistance.

cheers,
Michael

---

### Post by julfi on 2009-01-07
Thank you for your reply,
3d acc is working properly, I also tried to switch from EXA to XAA but it doesn't solve the problem.

here are logs and configs


Xorg.0.log
[http://pastebin.com/m67a353f7]("http://pastebin.com/m67a353f7")

Xorg.conf
[http://pastebin.com/m26bb374b]("http://pastebin.com/m26bb374b")

glxinfo
[http://pastebin.com/m2cbb5f44]("http://pastebin.com/m2cbb5f44")

thanks

---

