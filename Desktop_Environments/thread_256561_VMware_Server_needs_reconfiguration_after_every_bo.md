---
title: "VMware Server needs reconfiguration after every boot"
date: 2006-09-13
forum: Desktop Environments
---

### Post by abelthorne on 2006-09-13
Hello,
I've installed VMware Server with no problem. All worked fine until a few days ago I installed KDE by adding the kubuntu-desktop package to my Ubuntu 6.06.1 system. I've had troubles using Gnome after that so I uninstalled KDE and had to manually remove some files (related to the Gtk2-Qt engine) to remove it completely.
I think I broke something in the system because since then, every time I boot the OS I have to reconfigure VMware Server.

I've seen other users having similar problems but it seemed to be elated to kernel versions. I didn't change anything to the kernel I use.

Any idea how to fix this problem ?

---

### Post by djdennie on 2006-09-13
I'm not sure if it's a bug or not.. but try deleting the file:

/etc/vmware/not_configured

I had the same prob.. you'll need to do it after every reboot. :(
It's faster than reconfiguring though.

---

