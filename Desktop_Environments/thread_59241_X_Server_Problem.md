---
title: "X Server Problem"
date: 2005-08-23
forum: Desktop Environments
---

### Post by Davidios on 2005-08-23
Hi everyone.

I've updated my Ubuntu to Breezy. When I reboot my computer I can't start. It has appeared:

>  I cannot start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem? 

I select "Yes"...

>  /etc/X11/X is not executable

I select "Ok"...

> I will disable this X server for now. Restart GDM when it is configured.

I've tried with "sudo dpkg-reconfigure xserver-xorg" but it don't work.

I have an Ati RADEON 9250 256 MB. What can I do?

---

### Post by plb on 2005-08-23
Well as the debian saying goes......welcome to unstable....or in this case....welcome to breezy  :) I would try reinstalling x-window-system-core perhaps and run xorgconfig manually

---

