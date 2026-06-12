---
title: "ndiswrapper fails: segmentation error"
date: 2005-12-27
forum: Desktop Environments
---

### Post by bulldogsay on 2005-12-27
well i have been using suse 10.0 for half a year and with all the new kernel and xorg come out, i decided to come to ubuntu. Yet everything worked fine except ndiswrapper.

all seems to work fine, but such as getting the driver working etc, but when it comes to modprobe ndiswrapper it goes bad...

firstly it says **segmentation fault**

in dmesg it says:
[B]
ndiswrapper (wrapper_init:1830): load ndiswrapper failed.[/B]

linux though doesn't crash and my broadcom / belkin pcmcia card's light is on but  cannot be used?

any way to solve this, as i have tried with breezy badger and it works fine?

---

### Post by kaamos on 2005-12-27
I suggest updating to the newest ndiswrapper since the installation is as simple as extracting the tarball and "make install". This might help.

---

### Post by az on 2005-12-27
[QUOTE=kaamos]I suggest updating to the newest ndiswrapper since the installation is as simple as extracting the tarball and "make install". This might help.[/QUOTE]

I think you need gcc3.4 to make a kernel module and if you do not have access to the internet to do that, you will have trouble.

Anyway, you can often fix this sort of problem by getting a more recent .inf file for your driver.  Ndiswrapper always develops with the most recent -  sometimes older .inf files are not compatible anymore.

---

