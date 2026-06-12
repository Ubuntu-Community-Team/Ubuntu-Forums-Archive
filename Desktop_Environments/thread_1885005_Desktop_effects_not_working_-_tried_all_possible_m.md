---
title: "Desktop effects not working - tried all possible methods"
date: 2011-11-22
forum: Desktop Environments
---

### Post by cvrprakash on 2011-11-22
Dear All,

I had installed ubuntu 11.10 2 days back and I am very well used all this 3D desktop and other efects in earlier ubuntu versions 10.04.

Can you please help me to get the fix. Please suggest a way out as I really don't want to leave Ubuntu 11.10 for this.

Thanks.

---

### Post by vangop on 2011-11-22
Do you have video drivers installed?
Check if the effects are enabled in ccsm (install compizconfig-settings-manager)

---

### Post by cvrprakash on 2011-11-22
Yes, I have Video Driver and Compiz is alraedy installed.


cvrprakash@cvrprakashX:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: D9M-20/PCI/SSE2/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

---

### Post by vangop on 2011-11-22
So what exactly do you experience?
I suggest also looking into ~/.xsession-errors , dmesg and /var/log/Xorg.0.log for some hints on what's going on wrong.

---

### Post by cvrprakash on 2011-11-22
Dear vangop,

Really I have no idea. I installed and enabled the desktop cube effects and other effects. Nothing really taking effect.
Did restart that also dint work.
Here with I'll attach the 3 files that you had requested. Kindly check in to it and share if you find anything you find interesting.

Thanks

---

### Post by cvrprakash on 2011-11-25
Guys,

Any one can assist me in this??
Thanks.

---

### Post by MG&amp;TL on 2011-11-25
Effects like the desktop cube will not work in 11.10; some will, but some won't.

This is mostly down to the new Unity interface. (the panel). It is not possible without a serious amount of effort and possible breakage to enable the desktop cube in the Unity interface. Sorry.

If you want your cube back, you can either stick with 10.04, or go to Mint. Or another distro without Unity.

---

### Post by thetruckinglife on 2011-11-27
yeah i had the same issues with 11.04 and 11.10 trying to use compiz fusion effects and other dekstop customizations it would just make the screen freeze and i would have to do a hard shutdown.
so i just keep using 10.10 as it suites me very well.

---

### Post by bluexrider on 2011-11-27
in terminal

sudo compiz --replace

see if that works temporarily

---

