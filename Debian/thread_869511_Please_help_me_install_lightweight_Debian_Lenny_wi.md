---
title: "Please help me install lightweight Debian Lenny with IceWM."
date: 2008-07-24
forum: Debian
---

### Post by kagashe on 2008-07-24
I have downloaded the following iso:
debian-LennyBeta2-i386-netinst.iso

and the following files from Debian Lenny:
vmlinuz
initrd.gz

to boot the iso from hard disc and install a lightweight Debian with IceWM.

In fact I have already installed the base system and at "select and install software" stage unchecked the Desktop. There was one more option "Standard system" which was also unchecked but I am curious to know what gets installed if it was checked. I did not uncheck the "Laptop" option.

It seems to me that part of the X system (except xserver) are already installed because commands like xrandr are available.

kagashe

---

### Post by kerry_s on 2008-07-24
i usually uncheck everything.
if you have the base already:
as root>
apt-get install xorg icewm
exit

as user>
startx

you can install slim if you want a light log in manager(apt-get install slim)

---

### Post by kagashe on 2008-07-25
> **kerry_s said:**
> i usually uncheck everything.
if you have the base already:
as root>
apt-get install xorg icewm
exit

as user>
startx

you can install slim if you want a light log in manager(apt-get install slim)Thanks. I have installed xorg icewm iceweasel slim and posting this using Iceweasel on Lenny.

I also did apt-get update and upgrade and found interesting difference between Ubuntu and Debian. Initially it had installed Kernel 2.6.24 but allowed upgrade to 2.6.25. Perhaps this is because Lenny is still under testing.

When I tried to install synaptic it was asking to install many additional packages, therefore, I decided to use apt-get or aptitude to install additional packages.

kagashe

---

### Post by kerry_s on 2008-07-25
> **kagashe said:**
> Thanks. I have installed xorg icewm iceweasel slim and posting this using Iceweasel on Lenny.

I also did apt-get update and upgrade and found interesting difference between Ubuntu and Debian. Initially it had installed Kernel 2.6.24 but allowed upgrade to 2.6.25. Perhaps this is because Lenny is still under testing.

When I tried to install synaptic it was asking to install many additional packages, therefore, I decided to use apt-get or aptitude to install additional packages.

kagashe

sorry, i been busy rebuilding a desktop computer, took me a while, i'm rusty. :)

i noticed on lenny by default it's installing recommends, i usually turn it off. i can't find my cheat sheet right now, so your going to have to google it. once you turn that off installing stuff won't pull in so much.

anyways apt-get is great to, you can put short cuts/alias's in your bash thingy.

---

### Post by tel93 on 2008-07-26
> **kagashe said:**
> Thanks. I have installed xorg icewm iceweasel slim and posting this using Iceweasel on Lenny.

I also did apt-get update and upgrade and found interesting difference between Ubuntu and Debian. Initially it had installed Kernel 2.6.24 but allowed upgrade to 2.6.25. Perhaps this is because Lenny is still under testing.

When I tried to install synaptic it was asking to install many additional packages, therefore, I decided to use apt-get or aptitude to install additional packages.

kagashe

use apt-cache search instead. I use it on my lightweight Openbox machine.

---

