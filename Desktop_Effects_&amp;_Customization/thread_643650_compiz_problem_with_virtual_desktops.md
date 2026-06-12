---
title: "compiz problem with virtual desktops"
date: 2007-12-18
forum: Desktop Effects &amp; Customization
---

### Post by opteek on 2007-12-18
I've tried a clean install twice now and am still getting this problem. I have a Sony Vaio VGN-NR110E and I have a fresh installation of Gutsy. I've  updated after installation and installed xserver-xgl, which is required for compiz to run. I also have the compiz-settings-manager. Anyways,I try to create four virtual desktops in General Settings (4 desktops, 4 horizontal, 1 vertical), and they show up as four desktops in the bottom right panel. When I click on one of the other desktops, one of two things happens: either I am taken to a desktop with no icons like I have on my original desktop, in this case the mouse selection box doesn't work but both gnome panels work and I can start applications; in the other case, I have just my wallpaper, no panels, no icons, no nothing, and I am stuck there until I kill the xsession.

One thing I have tried doing on the second install was making sure I actually had four virtual desktops in metacity before starting up compiz. The metacity virtual desktops work fine, btw. The first time I did this, it seemed to work and I could actually change virtual desktops in compiz. I then enabled the e 3d cube and rotate cube plugins, which worked except for one thing. Namely, the four virtual desktops in compiz did not represent sides of the cube. It seemed to be that each virtual desktop had it's own cube, if that makes sense. Anyways, that stopped working altogether and now I am back to the original problem, so I am running compiz with one virtual desktop and things are working fine, but I would really like to be able to have a cube with four desktops.

---

### Post by john.nicholls on 2007-12-18
In the general Compiz settings, try:
Horizontal virtual size: 4
Vertical virtual size: 1
Number of desktops: 1

---

### Post by h8tisf8t on 2007-12-18
I'm a newbe to ubuntu. I have 7.10 installed on virtualbox and it works fine but i can't get the desktop effects to work. It won't let me change the settings from none to custom or any other choice. I have nvidia. Host is Vista

---

