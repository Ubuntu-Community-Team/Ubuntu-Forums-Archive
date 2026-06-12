---
title: "3d accel woes"
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by JELO on 2007-04-03
Hey guys,
Basically I had CS:Source and WoW working fine.  I decide to goof around with XGL and Compiz last night.  Don't know what I did exactly but I managed to fubar 3d acceleration it seems.  I get the error message that 3d acceleration can't be started when I try to ope WoW.  I tried apt-get autoremove to uninstall all the compiz stuff that I installed, 

compiz compiz-extra compiz-plugins compiz-extra-plugins gnome-compiz-manager gnome-compiz-manager-extra xserver-xgl

uninstalled nvidia-glx reinstalled, using my old xorg.conf file etc.

I did notice that removing xserver-xgl didn't go over well.  Apparently my system is running that now instead of metacity?  Not sure exactly, any who I need 3d acceleration back.  I'm running a 6600 btw.

Edit:  I ran the glxinfo command and notice that it says no by direct rendering.  I am able to run glxgears though.

---

### Post by H3g3m0n on 2007-04-03
It sounds like you need to fix your nvidia drivers if direct rendering is saying no.

glxgears will run without direct rendering, they will just use software instead and be much slower.

Metacity is a window manager where as xserver-xgl is a xorg server, Metacity can run on top of it without problems but Beryl/Compiz replace Metacity. I don't believe the nvidia drivers need xgl to do hardware acceleration for Beryl and such anymore.

Make sure that you are using the nvidia driver in xorg and not the nv driver and the glx is initilizing correctly. Check in /var/log/Xorg.0.log for any lines with EE or WW, or phrases such as glx or nvidia.

---

### Post by DealerMan on 2007-04-03
I don't know if this will help you Jelo, but it sure saved my hide.  Here's a link that'll load your nVidia driver without pain or discomfort.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


Good Luck, hope this helps.

---

### Post by xopher on 2007-04-03
Just trying to clarify:

When you have XGL enabled (logged into a xgl session) direct rendering will be disabled, effectively making any 3d-game malfunction. This is because the direct rendering is used by XGL, which is a different layer, on top of X, and there's no direct rendering available for the X server. (This is how I've understood this)

Anyway, as you have nvidia, you don't  have to worry about this. All you need, to get Beryl/compiz to work, is a 9x.xx series driver, and beryl/compiz of course. No need for XGL.

---

