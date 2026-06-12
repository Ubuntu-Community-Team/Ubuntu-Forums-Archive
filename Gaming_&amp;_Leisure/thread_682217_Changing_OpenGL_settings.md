---
title: "Changing OpenGL settings"
date: 2008-01-29
forum: Gaming &amp; Leisure
---

### Post by phoenix5002 on 2008-01-29
Is there a way to change graphical settings for fullscreen applications, such as mipmap quality and anisotropic filtering ect...

---

### Post by Melcar on 2008-01-29
I guess you mean with open source drivers?  I would like to know too in that case.  I guess it would be as simple as adding a few parameters in xorg.conf, but I have no idea how.

---

### Post by markharding557 on 2008-02-08
think you need restricted drivers to run opengl
there may be a control panel for opengl settings(there is for nvidia)never used ati so don't know on that

---

### Post by BLTicklemonster on 2008-02-08
If it's nvidia, your best bet is to use envy. Otherwise, go to applications, add remove, and at the top right, change it to where it will show everything available (sorry, not at my buntu box right now), then scoll down to ubuntu restricted, install all of that. Now go to system, administration, restricted drivers, and click on the one that shows up for your video card, and install it.

Reboot, and then use terminal

sudo nvidia-settings

and voila


If it's ati, buy an nvidia card.

---

