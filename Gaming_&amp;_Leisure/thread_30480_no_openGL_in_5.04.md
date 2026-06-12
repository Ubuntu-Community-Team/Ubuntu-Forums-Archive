---
title: "no openGL in 5.04"
date: 2005-04-28
forum: Gaming &amp; Leisure
---

### Post by questionasker on 2005-04-28
i have a Celeron (i know i know, but it works alot better than my old processor) 2.0 Gig processor, and an Nvidia Geforce FX 5200 128 MB AGP video card. and Hoary 5.04 updated through today (DSL modem!!)

i was hoping this would be decent enough for a little gaming, but im obvioculy not doing somehting right...

installed the nvidia drivers whatever from synaptic, and rebooted X, ran "glxgears" and got frame rates if about 180...

i used to run tuxracer fine with a 16Meg video card and a 700Mghz processor, so i know thiis new machine shoul be able to.

what are i not doing? i know nvidia has pretty good linux support and official drivers, but so far i just cant get the FPS im looking for.



anyone who could point me in the right direction i would be eternally grateful to.

---

### Post by jdodson on 2005-04-28
[QUOTE=questionasker]i have a Celeron (i know i know, but it works alot better than my old processor) 2.0 Gig processor, and an Nvidia Geforce FX 5200 128 MB AGP video card. and Hoary 5.04 updated through today (DSL modem!!)

i was hoping this would be decent enough for a little gaming, but im obvioculy not doing somehting right...

installed the nvidia drivers whatever from synaptic, and rebooted X, ran "glxgears" and got frame rates if about 180...

i used to run tuxracer fine with a 16Meg video card and a 700Mghz processor, so i know thiis new machine shoul be able to.

what are i not doing? i know nvidia has pretty good linux support and official drivers, but so far i just cant get the FPS im looking for.



anyone who could point me in the right direction i would be eternally grateful to.[/QUOTE]

try this: [http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)

not sure if "installed the nvidia drivers whatever from synaptic" means you got it configured correctly.

---

### Post by questionasker on 2005-04-28
[QUOTE=jdodson]try this: [http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)

not sure if "installed the nvidia drivers whatever from synaptic" means you got it configured correctly.[/QUOTE]
 yeah, thats what im asking. what do i configure? where do i change stuff?

---

### Post by domesticatewhat on 2005-04-28
do this from root after you have killed x

I think you:

sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-config enable
sudo dpkg-reconfigure xserver-xorg (select nvidia instead of nv and follow the page through)

That is how I do it anyways and everything is working fine here. You might want to check my commands again, though.   :roll:

---

### Post by questionasker on 2005-04-29
[QUOTE=domesticatewhat]do this from root after you have killed x

I think you:

sudo apt-get install nvidia-glx nvidia-settings
sudo nvidia-config enable
sudo dpkg-reconfigure xserver-xorg (select nvidia instead of nv and follow the page through)

That is how I do it anyways and everything is working fine here. You might want to check my commands again, though.   :roll:[/QUOTE]
 it was sudo nvidia-glxlconfig enable

thanks, but i tried that, ans i still dont get the FPS...

---

### Post by questionasker on 2005-04-29
[QUOTE=jdodson]try this: [http://ubuntuforums.org/showthread.php?t=25723](http://ubuntuforums.org/showthread.php?t=25723)

not sure if "installed the nvidia drivers whatever from synaptic" means you got it configured correctly.[/QUOTE]
 glxgears
Error: Could not open /dev/nvidiactl because the permissions
are too resticitive.  Please see the FREQUENTLY ASKED QUESTIONS
section of /usr/share/doc/NVIDIA_GLX-1.0/README for steps
to correct.
Segmentation fault


thats what i get whne i try to run glxgears... any ideas?

---

### Post by Professor X on 2005-04-29
```
sudo chmod 666 /dev/nvidia*
```

---

### Post by questionasker on 2005-04-30
[QUOTE=Professor X]```
sudo chmod 666 /dev/nvidia*
```[/QUOTE]
 that seems to have done the trick. now i dont get the error message, and get 1750+ FPS from glxgears... now to try a lil Quake3Arena... lol

---

### Post by graabein on 2005-05-05
I've tried nvidia-glx-config enable and dpkg-reconfigure xserver-xorg.

glxgears
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
1185 frames in 5.0 seconds = 237.000 FPS
1130 frames in 5.0 seconds = 226.000 FPS

glxinfo | grep render
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

lsmod | grep nv
nvidia               3923388  0
agpgart                31784  2 intel_agp,nvidia

Any ideas?

---

