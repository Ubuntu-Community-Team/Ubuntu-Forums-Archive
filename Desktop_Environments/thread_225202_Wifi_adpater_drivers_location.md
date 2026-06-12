---
title: "Wifi adpater drivers location"
date: 2006-07-29
forum: Desktop Environments
---

### Post by Endow on 2006-07-29
Oka can someone explain me how Dapper Drake now recognizes my wifi adpater when none of the old versions did?How come I haven't got to install anything?

Does it use ndiswrapper on the background or are there some special drivers for Linux created by the communitty(seeing as how my D-Link wifi adapter is no longer suported by D-Link)??

Is there any way I can simply import whatever files are responsible for the acceptance of the adapter from Ubuntu to another distro?(I'm currently checking some other distros out...)

Where are the files located?

---

### Post by Dr. Nick on 2006-07-29
unless you set up ndiswrapper then it wont be used.

All the drivers are built into the kernel, With dapper came a upgraded kerenel which probbaly includes your drivers when the old beezy kernel didnt.

Run this command and find out what driver your wifi is using, If it is a usb card look at the "usbcore" line

lsmod

That is the name of the dirver, then run 

locate *name*

and you will see where the file is. It is usually something like /src/kernelxx/drivers/net/wireless

You can try and save the driver files, but they wont work with any other kernel versions so say you have kernel 2.6.15-26-k7 on dapper now and you install say fedora at kernel 2.6.15-25-k7 then then dapper files wont work, But if you find a distro with the same kernel you have now they should already be included,

---

### Post by Endow on 2006-07-29
Mepis is based on Ubuntu right?Doers that mean it will probably suport the driver?

What about VectorLinux?

---

### Post by Dr. Nick on 2006-07-29
not sure if its based off it or not. so not sure if it would work.

in dapper type **uname -r **into a terminal and that will tell you the kernel you are running, so when you are looking at other disrtors features look and see what kernel they mention and make sure it is atleast the same ver of the daper, if not newer.

If i recall I think vector linux uses a older kernel, not sure though

---

