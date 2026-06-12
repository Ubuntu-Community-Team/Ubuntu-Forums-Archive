---
title: "ATI 8.42 Performance increases?"
date: 2007-10-27
forum: Gaming &amp; Leisure
---

### Post by quadomatic on 2007-10-27
Hey, I just upgraded to the newest ATI driver, so now I got AIGLX support :D

However, I don't know what kind of performance increase I'm getting, since I didn't really check before I upgraded.

What kind of performance increases is everyone else getting? 

Any better GLSL support so you can play games like Half-Life 2 in Direct X 9 mode, or better support so that people can play games like Max Payne 2 with pixel shaders on without a ton of glitches?

I'm downloading the Enemy Territory: Quake Wars demo right now. I don't think I'll be able to run it very well, as my system's processor and memory aren't all that great (check my sig), but I'll try it and compare the performance in linux to the performance to Windows.

---

### Post by jack handy on 2007-10-27
how do i check if this driver installed properly?  i went through all the motions (got the ati-driver-installer-8.42.3-x86.x86_64.run file, ran it, clicked ahead and got the confirmation), but i dont see any differences.. 

 i still cant switch to "Normal" visual effects in the Appearance/Visual Effects tab.. i get "The Composite extension is not available" error

any help would be appreciated.

---

### Post by quadomatic on 2007-10-27
> **jack handy said:**
> how do i check if this driver installed properly?  i went through all the motions (got the ati-driver-installer-8.42.3-x86.x86_64.run file, ran it, clicked ahead and got the confirmation), but i dont see any differences.. 

 i still cant switch to "Normal" visual effects in the Appearance/Visual Effects tab.. i get "The Composite extension is not available" error

any help would be appreciated.

You have to edit your /etc/X11/xorg.conf file. Find the line that says "Composite "0"" or something like that, and comment it out. It should be towards the bottom of the file, or at least it is for me.

Then you should hit ctrl+alt+backspace, or maybe just reboot. Type fglrxinfo in the terminal and make sure it says its using ATI in the vendor string, not MESA.

---

### Post by jack handy on 2007-10-27
yeah, it says MESA :(  what do i have to do to change that?

---

### Post by quadomatic on 2007-10-27
> **jack handy said:**
> yeah, it says MESA :(  what do i have to do to change that?

did you run aticonfig --initial?

Check the /etc/X11/xorg.conf

Look under the Device section. If the driver says "ati", or something else, change it to "fglrx"

Actually, follow this guide too:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by jack handy on 2007-10-27
i ran the aticonfig --initial

~$ sudo aticonfig --initial
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0

here's what my Device section looks like

Section "Device"
	Identifier  "Generic Video Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

---

### Post by jack handy on 2007-10-27
wait, there's another Device section in there that says

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

---

### Post by quadomatic on 2007-10-27
hmm...I'm not really sure what you can do with that...I'd delete the section bout Vesa, but I'd rather by careful to not break your system.

---

### Post by jack handy on 2007-10-27
alright, so after a little messing around,  i've got just

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

in my xorg.conf file..

i've still got this in fglrxinfo, though:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

hmmm..  i'll check out the wiki to see if i can find anything there, though.  thanks :)

---

### Post by quadomatic on 2007-10-27
> **jack handy said:**
> alright, so after a little messing around,  i've got just

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection

in my xorg.conf file..

i've still got this in fglrxinfo, though:

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

hmmm..  i'll check out the wiki to see if i can find anything there, though.  thanks :)

[http://wiki.cchtml.com/index.php/Troubleshooting#No_3D_acceleration](http://wiki.cchtml.com/index.php/Troubleshooting#No_3D_acceleration)

Try following that guide for troubleshooting this problem. It's worked for me before.

---

### Post by jack handy on 2007-10-27
lol after the whole thing.. still getting the mesa in the fglrxinfo :lolflag:

now i'm just obsessed with this

---

### Post by jack handy on 2007-10-27
ok, after a lot of blood, sweat and tears, i've got 

~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6958 Release


please tell me thats what i'm supposed to have lol

---

### Post by ricosrealm on 2007-10-27
I'm not really getting good performance with desktop effects... actually worse performance than fglrx and XGL indirect rendering.  I don't know about GL apps, but the fact that firefox and other apps that use pixmaps are very slow under Compiz kinda defeats the purpose of the driver update for me :(  I have checked  that DRI is enabled and compositing is enabled and I am using ATI glx.

---

### Post by Supersaiyan.IV on 2007-10-27
> **quadomatic said:**
> Hey, I just upgraded to the newest ATI driver, so now I got AIGLX support :D

However, I don't know what kind of performance increase I'm getting, since I didn't really check before I upgraded.

What kind of performance increases is everyone else getting? 

Any better GLSL support so you can play games like Half-Life 2 in Direct X 9 mode, or better support so that people can play games like Max Payne 2 with pixel shaders on without a ton of glitches?

I'm downloading the Enemy Territory: Quake Wars demo right now. I don't think I'll be able to run it very well, as my system's processor and memory aren't all that great (check my sig), but I'll try it and compare the performance in linux to the performance to Windows.

Well yeah, back to the main topic of this thread.
Installed 8.42.3 with some tackling, but got that sorted out. 

I've tried playing Quake3 (fullscreen! and compiz still running in background) with highest graphics settings on, 1024x768, got about 100fps constant which I think is good. It topped around 120fps, and at worst it's 80fps,

Otherwise it's following:
> 
kuba@MATRIX-A1:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X300
OpenGL version string: 2.0.6958 Release

kuba@MATRIX-A1:~$ glxgears 
6310 frames in 5.1 seconds = 1247.611 FPS
4068 frames in 5.0 seconds = 806.200 FPS
3729 frames in 5.1 seconds = 726.628 FPS
3390 frames in 5.2 seconds = 655.808 FPS
4520 frames in 5.1 seconds = 889.208 FPS
5989 frames in 5.1 seconds = 1181.065 FPS
6215 frames in 5.1 seconds = 1209.070 FPS

kuba@MATRIX-A1:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
1279 frames in 5.0 seconds = 255.800 FPS
1072 frames in 5.0 seconds = 214.400 FPS
1063 frames in 5.0 seconds = 212.600 FPS
1120 frames in 5.0 seconds = 224.000 FPS


Note that the fps is faster at beginning, then it seems something is halting the fps from growing. I know DRI can't form a buffer, because of some bug, i know this because mplayer complains about that when DRI is enabled.

Sometimes:
> 
kuba@MATRIX-A1:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer


Returns a segmentation fault, and core dumped. And sometimes it doesn't, I know that happens because some applications turn off DRI according to their needs, and it can therefore be easily activated by running a DRI enabled prog.

Mplayer Error:
> 
[gl] could not acquire buffer for dri
Excpect a _major_ speed pentaly


The performance halts noticeable in the "benchmarks" are noticeable in the compiz effects aswell. They are very slow and buggy at times. And I believe it's because of the missing DRI buffer, also mentioned above.

The mplayer direct rendering error appears for all possible mplayer  OpenGL settings, and other settings with double buffering. If anyone has a solution I'm all ears.

peace

---

### Post by Peaceable Frood on 2007-10-27
> Using GLX_SGIX_pbuffer
3845 frames in 5.0 seconds = 769.000 FPS
4037 frames in 5.0 seconds = 807.400 FPS
4300 frames in 5.0 seconds = 860.000 FPS
4397 frames in 5.0 seconds = 879.400 FPS
4385 frames in 5.0 seconds = 877.000 FPS
4389 frames in 5.0 seconds = 877.800 FPS


This is on a x1400. I have noticed a speed increase from 8.40.3. 

If you want to increase performance when using compiz add TexturedVideo "true" to your device section and that should help.

[These options may help too](http://compiz.org/ATI)

---

### Post by Supersaiyan.IV on 2007-10-27
> **Peaceable Frood said:**
> This is on a x1400. I have noticed a speed increase from 8.40.3. 

If you want to increase performance when using compiz add TexturedVideo "true" to your device section and that should help.

[These options may help too](http://compiz.org/ATI)

Thx a lot, now I'm at:

> 
kuba@MATRIX-A1:~$ fgl_glxgears 
Using GLX_SGIX_pbuffer
1966 frames in 5.0 seconds = 393.200 FPS
1981 frames in 5.0 seconds = 396.200 FPS
1989 frames in 5.0 seconds = 397.800 FPS


Which is good for a x300 64mb gfx card.

I'm off to bed, it's 03:30 new time Oo
nite

peace

---

### Post by glosman15 on 2007-10-27
> **Peaceable Frood said:**
> This is on a x1400. I have noticed a speed increase from 8.40.3. 

If you want to increase performance when using compiz add TexturedVideo "true" to your device section and that should help.

[These options may help too](http://compiz.org/ATI)

Would you mind posting a copy of your xorg.conf? I have the same card (x1400) and I can't anywhere near those fgl_glxgears outputs scores.

---

### Post by jack handy on 2007-10-27
i'm trying to get the same thing i did this afternoon done on my wife's laptop and its not working :mad:

what's the chances that this driver will be available to install through the update manager soon?

---

