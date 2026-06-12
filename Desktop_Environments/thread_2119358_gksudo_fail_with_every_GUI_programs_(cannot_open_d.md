---
title: "gksudo fail with every GUI programs (cannot open display)"
date: 2013-02-23
forum: Desktop Environments
---

### Post by Jnfn on 2013-02-23
Hello everyone!

I've this weird problems on my ubuntu 12.04.2 machine with gnome-shell 3.4, gnome3 PPA and some backports from quantal:

gksudo doesn't work anymore and it just says "cannot open display" when I try "gksudo gedit", but if I try "gksudo nautilus" it just silently fails. same for almost every other GUI programs.
If I do "sudo su" and then "nautilus" same behaviour.
pkexec works smoothly
echo DISPLAY says :0
under unity same behaviour
already checked forums allaround

I didn't change anything manually in the recent period but a "normal" upgrade changed all the xorg packages under the rule of the xserver-xorg-renamed so all of these packages now has a -lts-quantal in their names. I can't confirm if the issue appear in that moment. 

Aside from that I can't install extensions from the website with any browser and I don't know if the issues are realted. 

thanks to anyone who can help

---

### Post by claracc on 2013-02-24
You has to have ppa's and backport software corresponding to your distro: precise pangolin. You cannot mix with software corresponding to the quantal quetzal release. Disable the quantal software in software sources as well as quantal backports. Then update your system

---

### Post by Jnfn on 2013-02-24
thanks, well actually, I didn't mix the repo. the xorg packeges ar just from "precise-update" repository branch so I think it's ok. indeed I've already ppa-purged the xswat-qlts-backport PPA. 

...I don't really want to reinstall everything and since i have separate home I could bump into the same problem after the reinstall. 
.. and I've already reset gnome settings. 
I think it's something related to X but I can't understand what is it and since that how to solve.

anyone any clues?

---

### Post by bogan on 2013-02-24
Hi!, **claracc**,

The 'lts-quantal' files and backports are all part of the standard 12.04.2 installation to permit the use of the 3.5.0-xx kernal, in place of the 3.2.0-xx kernal still used in 12.04.1, and the updated version to 12.04.2.

[COLOR=Red]DO NOT delete them!! nor uninstall them!![/COLOR]

Chao!, **bogan**.

---

### Post by Jnfn on 2013-02-24
thanks Bogan, 

you just confirmed my suspect, so apparently everything is fine. 
Any clue where the problem is?

---

### Post by bogan on 2013-02-24
> **Jnfn said:**
> thanks Bogan, 

you just confirmed my suspect, so apparently everything is fine. 
Any clue where the problem is?Not in any detail, its a bug, dependancies being called that do not exist or have not been updated.

Frankly, I am amazed that the upgrade works as well as it does, and so few programs fail to run. Unfortunate that some  of them are certain nvidia driver installers and 'Steam'.

Chao!, **bogan**.

---

### Post by Jnfn on 2013-02-25
> **bogan said:**
> Frankly, I am amazed that the upgrade works as well as it does, and so few programs fail to run. Unfortunate that some  of them are certain nvidia driver installers and 'Steam'.

Chao!, **bogan**.

I'm using the 3.5 kernel and via terminal the installation of nvidia driver worked smoothly, I don't know about steam..it's an old laptop :)

---

