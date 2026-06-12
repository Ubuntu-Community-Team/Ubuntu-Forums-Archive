---
title: "Shutdown and Reboot buttons missing from KDE logout menu"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by Ashex on 2007-04-22
I recently got beryl up and running in feisty kubuntu.

One of the issues I'm having is getting the shutdown, reboot, standby, etc. buttons to show up in the logout window. 

I followed the guide in the beryl wiki and I haven't had much luck trying the tweaks they recommended. Anyone have ideas on how to get those buttons back?

---

### Post by lazyrussian on 2007-04-23
I've had the same problem. I've been using the terminal to shutdown or sometimes I just log out and then shutdown from the login screen.

None of the tweaks on the beryl wiki have worked.

---

### Post by g.gavro on 2007-04-24
Same problem here as well... Goes for Beryl as well as Compiz (KDE). Only solution for now is to place some shutdown/reboot icons on the desktop/panel....

---

### Post by lazyrussian on 2007-04-26
*bump*

---

### Post by DizzyTech on 2007-04-28
Are you using KDM or GDM as the login manager?  'Cause I get this problem from using KDE and GDM.  I just go back to the login screen and shut down from there.

---

### Post by sin on 2007-04-29
try installing the drivers with envy [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
it's a very tidy installer and it did the trick for me.

---

### Post by theonlykman on 2007-05-01
woah, same thing is happening to me with gdm. I was just messing around with a login theme (actually, managing to manually add a user list to it). I had no idea what I was doing, so I did a little trial and error...modify the code, logout, modify the code logout etc...I got it working perfectly...except all of a sudden poof! I lose the shutdown and reboot options in the login and also in the shutdown menu while logged in.

Any ideas?

---

### Post by bartvbeek on 2007-06-16
What worked for me was, using gdm instead of kdm. This can be done by running 

sudo dpkg-reconfigure gdm

---

