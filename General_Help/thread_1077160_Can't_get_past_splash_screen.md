---
title: "Can't get past splash screen?"
date: 2009-02-22
forum: General Help
---

### Post by dj9928 on 2009-02-22
When I go to run Ubuntu or any other distro for that matter I can't get past the splash screen and the progress bar freezes at about 20% and thats it, Doesn't matter if you install or run live CD, I have tried tapping keys, I have tried safe graphics, I have tried irqpoll but nothing works, Any advice very much appreciated.

The laptop is a

Fujitsu Siemens Esprimo V6515
2.0ghz Celeron 575 processor
3GB Ram
160GB HDD
Nvidea GeForce 8200
Atheros Wireless Card
I can't figure out the issue,

---

### Post by geirha on 2009-02-22
At the boot menu of the ubuntu CD, hit F6 to see the "kernel"-line. At the end of the line there are two words: quiet splash. Remove those two words and hit enter. This will make the splash screen not appear  during boot, and instead print a lot of text about what the kernel is trying to do. What is it trying to do when it freezes?

---

### Post by dj9928 on 2009-02-22
Ok here is the screen where it freezes.

[IMG]http://img232.imageshack.us/img232/7985/sdc10055.jpg[/IMG]

---

### Post by geirha on 2009-02-22
Seems to be the driver for atheros wireless that makes it freeze. I found a bug on it here:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/276445](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/276445)

---

