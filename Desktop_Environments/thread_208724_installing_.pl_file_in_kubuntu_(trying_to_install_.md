---
title: "installing .pl file in kubuntu (trying to install VMware)"
date: 2006-07-04
forum: Desktop Environments
---

### Post by zeltak on 2006-07-04
Hi guys

im trying to install a VMware trial workstation. the installer has a .pl extension (vmware-config.pl). ive tired opening it from the terminal and from the GUI yet no matter what i do i cant seem to get it to work. in the GUI it does nothing or opens with an editor and in the GUI i get this:

-su: vmware-config.pl: command not found

can anyone please help me intsall vmware?

thx 

zeltak

---

### Post by Lokken on 2006-07-04
sudo chmod a+x vmware-config.pl
sudo ./vmware-config.pl

or... just

sudo perl vmware-config.pl

That should do the trick, I think.

Enjoy.

---

