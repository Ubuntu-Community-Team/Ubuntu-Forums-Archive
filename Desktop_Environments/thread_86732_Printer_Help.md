---
title: "Printer Help"
date: 2005-11-06
forum: Desktop Environments
---

### Post by Ingla on 2005-11-06
Hello.

I have an HP 1315 All-in-One (recognized by system as 1310).

It printed in Ubuntu "out of the box"...until I tried to set it up to run the scanner also.

I was trying to follow these instructions:
----------------------------------------------------------

[COLOR="Red"]
make sure the hp psc 1315 is plugged in.

#1 Make sure you have the following installed:


libsane-hpoj-0.91-9
hpoj-0.91-9
hpijs-1.6-2

#2 on a terminal, type 'ptal-init setup', and answer the questions (its short and
straightforward)

#3 now you wanna type 'ptal-init start' to start the scanner

#4 to test the scanner type in scanimage -d hpoj:mlc:usb:psc_1310_series_ --test

(if you don't have the 1315/1310 replace it that line with the device name:
scanimage -d hpoj:device --test

to find out the name of your device type 'scanimage --list-devices' and replace
the device name in the previous command to test it...

#5 now startup a scanning program like xsane or kooka :

For Kooka -
kooka -d hpoj:mlc:usb:psc_1310_series_

For Xsane -
xsane hpoj:mlc:usb:psc_1310_series_

THATS IT!![/COLOR]
-----------------------------------------------------------

After I did that, the scanner worked but the printer didn't.

Problem is the neccessary files are not available (espcially libsane-hpoj, which has no version installed). So I downloaded some .rpm's.

When I try to convert one, using "sudo alien package_file.rpm" I get:

[COLOR="Red"]sudo: alien: command not found[/COLOR]

What's going wrong?

Thanks.

---

### Post by kperkins on 2005-11-06
Is alien installed on your system?

---

### Post by Ingla on 2005-11-06
Hi.

Thanks for the reply. That's a newbie for you. I didn't know it needed to be installed...thought it was a generic command.

Anyway, it generated a deb which I tried to install, but got this:
-------------------------------------------------------------------------

[COLOR="Red"]sudo dpkg -i Desktop/libsane-hpoj_0.91-10_i386.deb
Selecting previously deselected package libsane-hpoj.
(Reading database ... 97646 files and directories currently installed.)
Unpacking libsane-hpoj (from .../libsane-hpoj_0.91-10_i386.deb) ...
dpkg: error processing Desktop/libsane-hpoj_0.91-10_i386.deb (--install):
 trying to overwrite `/usr/lib/sane/libsane-hpoj.so', which is also in package h poj
Errors were encountered while processing:
 Desktop/libsane-hpoj_0.91-10_i386.deb[/COLOR]


--------------------------------------------------------------------------
Can anyone tell me what the problem is or what I can do about it?

Printer status: when I try to copy nothing happens. Then I turn off the printer and turn it back on. Printer manager says it's off...I restart it and it prints. This ***is*** driver trouble isn't it?

---

### Post by kperkins on 2005-11-06
[QUOTE=Ingla]Hi.

Thanks for the reply. That's a newbie for you. I didn't know it needed to be installed...thought it was a generic command.

Anyway, it generated a deb which I tried to install, but got this:
-------------------------------------------------------------------------

[COLOR="Red"]sudo dpkg -i Desktop/libsane-hpoj_0.91-10_i386.deb
Selecting previously deselected package libsane-hpoj.
(Reading database ... 97646 files and directories currently installed.)
Unpacking libsane-hpoj (from .../libsane-hpoj_0.91-10_i386.deb) ...
dpkg: error processing Desktop/libsane-hpoj_0.91-10_i386.deb (--install):
 trying to overwrite `/usr/lib/sane/libsane-hpoj.so', which is also in package h poj
Errors were encountered while processing:
 Desktop/libsane-hpoj_0.91-10_i386.deb[/COLOR]


--------------------------------------------------------------------------
Can anyone tell me what the problem is or what I can do about it?

Printer status: when I try to copy nothing happens. Then I turn off the printer and turn it back on. Printer manager says it's off...I restart it and it prints. This ***is*** driver trouble isn't it?[/QUOTE]
try sudo dpkg -i --force-overwrite Desktop/libsane-hpoj_0.91-10_i386.deb
It probably is driver trouble, also.  Scanners and all-in-ones are not very well supported under linux. (the Xsane project is an excellent project though, I'm not trying to disparrage them in iany way.)

---

### Post by Ingla on 2005-11-06
Thanks.

That did it.

Still working strangely. I scanned a page and that worked fine. Then tried to print, but it wouldn't work. I turned the printer off (physically) and turned it back on. Then, successfully printed two documents. 

It seems running the scanner kills the printer, but it's not hard to correct.

I'm wondering whether to try further to get this working normally or whether that's about all I can expect without messing something up.

Any ideas?

---

