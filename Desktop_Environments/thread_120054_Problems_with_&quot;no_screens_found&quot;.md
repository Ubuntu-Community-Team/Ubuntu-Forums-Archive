---
title: "Problems with &quot;no screens found&quot;"
date: 2006-01-20
forum: Desktop Environments
---

### Post by kpurcell on 2006-01-20
I am trying to Install Ubuntu Linux for amd64 on my Emachines T6212 computer.  It has an ATI x700 PCIe card hooked up to two 17 inch CRTs.  One is a Philips 107S and the other is an HP Pavilion mx70.  I get the following errors after ubuntu gets to where it is finished with all the text lines that run so fast you can read hardly any of them to the pretty brown screen with its list of entries and ok after each.  It then craps out and says it cannot boot and offers to show a log file for the xserver.  I read it and most of it means nothing.  But here is what you probably need to help me.

it says a couple of time "No symbols found" and then "fatal error no screens found."

Any help would be nice.  Also, how do I make grub default to boot Windows so that when my kids turn on the pc it goes right their for them?

---

### Post by cayamara on 2006-01-20
[QUOTE=kpurcell]It then craps out and says it cannot boot and offers to show a log file for the xserver.  I read it and most of it means nothing.  But here is what you probably need to help me.

it says a couple of time "No symbols found" and then "fatal error no screens found."

Any help would be nice.  Also, how do I make grub default to boot Windows so that when my kids turn on the pc it goes right their for them?[/QUOTE]
For the XServer problem, more info would be appreciated. Please post
```
/var/log/Xorg*log
``` and ```
/etc/X11/xorg.conf
```
The first file should be the error log, the second your config file.

For grub default boot, you just have to edit the "default" parameter in /boot/grub/menu.lst.

---

