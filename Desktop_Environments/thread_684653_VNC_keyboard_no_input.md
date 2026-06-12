---
title: "VNC keyboard no input"
date: 2008-02-01
forum: Desktop Environments
---

### Post by Gloppie on 2008-02-01
Hello,
VNC clients (vncviewer, xvnc4viewer) will not accept keyboard input for either the server or the password dialog. This happens even trough the TSclient front end . If I open a term window and type "vncviewer [ipofthemachine]" the password input window pops up but I can not type in it. Using a saved .rdp profile in TSclient has the same effect. This is with Gnome btw, mouse works fine, I can click Help Cancel or close and windows respond fine.
All other programs are working fine.

On a side note, I have been trying to remove and re install the VNC apps but Synaptic tells me that to remove vncviewer it will remove ubuntu-desktop too, and that package is noted as a do not remove one. Any help or pointers greatly appreciated.

Otherwise so far Ubuntu rocks !

---

### Post by Gloppie on 2008-02-01
I also notice that the window decoration is different on the "action cancelled" Ok button window that pops when I hit the Top right X to close the non functioning dialog.
This may be related; I will try to find a place to put some screen grabs up for your attention.
Thanks

---

### Post by Gloppie on 2008-02-08
Well after more research I found that it is a know bug...
Bug #122654 in compiz (Ubuntu)
Thanks.

---

### Post by krakerjak on 2008-02-20
Anyone know of a workaround?

---

### Post by krakerjak on 2008-02-20
Nevermind, I found this workaround from launchpad.  It seems to work.

> 
 J Wood wrote on 2007-10-25: (permalink)

I filed recently a duplicate bug (didn't find this thread) at [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156827](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/156827).

Here's one quick work-around for entering data in a data entry field when using vncviewer (the alt-tab didn't work for me if the other application covered vncviewer):

1.) Click on an open application that is adjacent to but not covering vncviewer (such as a Tomboy note, which is how I found out the workaround)
2.) Click back on the data entry field of vncviewer; you can then enter data.


---

