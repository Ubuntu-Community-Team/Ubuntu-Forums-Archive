---
title: "&quot;Secret&quot; boot loader"
date: 2010-09-13
forum: Desktop Environments
---

### Post by Tsun on 2010-09-13
I was just wondering if it's possible to hide the boot loader :D

I mean so that it boots to windows 7 normally like any windows system, but unless you do some special action(such as holding some F key), it will open the boot loader and allow you to select ubuntu and other options.



edit
Wow thanks for fast replies :D
I'm not used to being replied within 24hours lately so i just went to play prototype lol
I don't want to bump anymore though.

---

### Post by Grenage on 2010-09-13
Yes, I believe you can set the timeout to 0, then hold down shift when the computer is booting (to see the grub menu).

Providing of course, it's your computer. :)

---

### Post by drs305 on 2010-09-13
Set GRUB_TIMEOUT=0 in /etc/default/grub.

Here are more detailed instructions, Section 4:
[http://ubuntuforums.org/showthread.php?t=1302743]("http://ubuntuforums.org/showthread.php?t=1302743")

You can also change the timeout from a GUI app called StartUp-Manager. For how to install and use it, click on the "SUM" link in my signature line.

---

