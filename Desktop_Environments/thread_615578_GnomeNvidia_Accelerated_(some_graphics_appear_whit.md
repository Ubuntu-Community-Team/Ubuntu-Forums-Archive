---
title: "Gnome/Nvidia Accelerated/ (some graphics appear white; outline of windows dissapeared"
date: 2007-11-17
forum: Desktop Environments
---

### Post by Rodents on 2007-11-17
Okay; I'm running Ubuntu 7.10; fresh clean install. When I first logged in it showed me this new restricted driver thing I've never seen before; so I clicked it. I enabled the nvidia accelerated graphics thing there; everything went smooth; I restarted..

but the first thing I noticed were the tooltip notification boxes showed up completely white, unable to do anything about them at all.. and when I try to run applications like terminal.. they appear white too; I installed java; it asked me to accept a session but that too turned up to be a white box; nothing but a white box.

Things like firefox and pidgin work though no problem

Also; it's hard to describe; but that outerlining thing on every window; with the main bar at top with the minimize maximize and close button is nowhere to be found on ANY window.. 

but performance wise; the graphics driver has made a world of difference..
is there any fix? I'd hate.. absolutely hate to give up performance like this..

---

### Post by overdrank on 2007-11-18
> **Rodents said:**
> Okay; I'm running Ubuntu 7.10; fresh clean install. When I first logged in it showed me this new restricted driver thing I've never seen before; so I clicked it. I enabled the nvidia accelerated graphics thing there; everything went smooth; I restarted..

but the first thing I noticed were the tooltip notification boxes showed up completely white, unable to do anything about them at all.. and when I try to run applications like terminal.. they appear white too; I installed java; it asked me to accept a session but that too turned up to be a white box; nothing but a white box.

Things like firefox and pidgin work though no problem

Also; it's hard to describe; but that outerlining thing on every window; with the main bar at top with the minimize maximize and close button is nowhere to be found on ANY window.. 

but performance wise; the graphics driver has made a world of difference..
is there any fix? I'd hate.. absolutely hate to give up performance like this..

Hi and you may need to add this to your xorg
Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
You can use the alt, F2 keys and enter this command ```
gksudo gedit /etc/X11/xorg.conf
```
Good luck and hope this helps.

---

### Post by rexxxlo on 2007-11-18
i have this problem now too i cant close the window of anything unless i do a right click and choose quit 

firefox has adapted to this by just moving up in the screen now there is a small bar at the bottom that i can see the desktop through  

what gives?

---

### Post by pdnick on 2008-03-15
I'm having this problem but I want to make sure I do this right...

Is there anywhere specifically in the xorg file I put this? Can I just add it to the bottom, I have yet to ever edit this by hand...

---

### Post by pdnick on 2008-03-15
As I just put up elsewhere I managed to get a "solution" by logging out and logging into Kubuntu. Gnome seems to of been hassling me.

---

### Post by overdrank on 2008-03-15
> **pdnick said:**
> As I just put up elsewhere I managed to get a "solution" by logging out and logging into Kubuntu. Gnome seems to of been hassling me.

HI and yes the above suggestion should be input in the device section of the xorg
Example
Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
EndSection

---

