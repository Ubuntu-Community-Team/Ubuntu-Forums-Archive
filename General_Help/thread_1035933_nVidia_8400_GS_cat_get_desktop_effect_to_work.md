---
title: "nVidia 8400 GS cat get desktop effect to work"
date: 2009-01-10
forum: General Help
---

### Post by mindxpert on 2009-01-10
I have installed Ubuntu 8.10 on HP Pavilion dv6000. I'm new at ubuntu!
Updated it using update manager(not sure what it was called) 
the problem is i cant activate desktop effects. Cant install nvidia drivers (8400GS), this is what i get when i type compiz in terminal : Cgecjubg fir Xgl:not present.
No whitelisted driver found aborting and using fallback: /user/bin/metacity
Window manager warning: GCong key '/apps/meacity/general/action_double_click_titlebar' is set to an invalid value

what can i do for it :S plz help  :confused:

Thx,
edi

---

### Post by gianluca.pettinello on 2009-01-10
Have you tried to enable the proprietary drivers?
Goto System/Administration Hardware Drivers

There you can enable and download the nvidia drivers 177 or 173.
If you are brave I suggest you to update to the drivers 180.18 which are much faster than the ones in official release.

To enable them:
sudo gedit /etc/apt/sources.list
add the following lines
deb [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu) jaunty main
then save and reload update manager

Gianluca

---

### Post by mindxpert on 2009-01-10
Thx for the reply.

I have tried Activating drivers 173 and 177 but it wouldnt activate them. I tried manual installing 180.22 on one of the threads but i failed. I dont remember the errors now because i'm running on xp on another pc. I'm reinstalling ubuntu on laptop and will try what u said.
I hope it works!

Edi

---

