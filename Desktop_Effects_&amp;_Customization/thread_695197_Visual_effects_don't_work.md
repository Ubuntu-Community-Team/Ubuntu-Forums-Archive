---
title: "Visual effects don't work"
date: 2008-02-12
forum: Desktop Effects &amp; Customization
---

### Post by snow_56767 on 2008-02-12
Hi,
   I've been trying to enable my visual effects but I always get a window saying
   
   Could not enable desktop effects

   I've tried installing compiz and typing compiz into the terminal. But it just doesn't work.
   I've made this simpler (I guess) by listing  my graphics card type:
   
   it is a nVidia10 ASUS V6600 GeForce 256 SDR with 32 MB of RAM
   My processor is a Intel Inside pentium 3 (coppermine)

   :(Help please!!!:(

---

### Post by arkara on 2008-02-12
have you installed the nvidia restricted drivers drivers??
judging by your card open a terminal and give
```
sudo apt-get install nvidia-glx-legacy
```
if the driver installs and nothing works again then give
```
sudo nvidia-glx-config enable
```
if again nothing works then try to install a newer driver. and if again nohting works then maybe your card is too weak to enable those effects

---

### Post by snow_56767 on 2008-02-12
Hi,
   I have installed the newer drive and enabled it and rebooted, nothing happened. It's weird because The description of the card says it is made for 3D effects. I found another forum that said to run compiz in the terminal. So I did and I got this
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0100 (rev 10) (prog-if 00 [VGA])
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault (core dumped)
not present. 
aborting and using fallback: /usr/bin/metacity 
```    
First what is Xgl and how do I get it. Second how would I fix this problem?
:)Thanks!:)

---

### Post by FrozenFox on 2008-02-12
XGL (kind of bad) and AIGLX (better) have to do with the video drivers / 3d capability. Compiz can work with either and will pick whichever one your system is set up with. You don't need to "get" aiglx really, it just needs to be enabled via having the nvidia drivers installed correctly.

Sounds like the usual story of.. well, just that: the video drivers not being installed correctly. Please open the terminal via start-->accessories, and type in glxinfo | grep direct  and then tell us whether direct rendering is enabled or not.

Please also try the guy above's advice on installing the drivers from the terminal, reboot, and report back. :)

---

### Post by snow_56767 on 2008-02-12
I'm back,
First LOL to what FrozenFox said. Second,    
I tried installing the nVidia drivers and restarted my computer. Still nothing. I just 
opened my terminal and typed ```
glxinfo | grep direct
``` like FrozenFox said to do
and I got this:
```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```
:grin: wow :grin:

---

### Post by FrozenFox on 2008-02-12
Lol, wow. Your video drivers are surely not installed correctly for some reason or xorg is setup wrong. But to make sure it's not just the lack of the glx module and to see if your video driver setup is going at all, please give us the output of:

cat /etc/X11/xorg.conf


Alternatively, if there's too much to copy n paste or that's a pain,  you can do:   cat /etc/X11/xorg.conf > ~/Desktop/xorg.txt  and attach that text file saved to your desktop to your response post for us.

I imagine your drivers might be installed, but they for some reason didn't set up your xorg file correctly, which should be an easy fix if that's the case.

---

### Post by snow_56767 on 2008-02-12
>  FrozenFox:
cat /etc/X11/xorg.conf >~/Desktop/xorg.txt
I did just that and now I'm giving that file to you [ATTACH]59531[/ATTACH]

---

### Post by FrozenFox on 2008-02-12
Puzzling. The drivers appear to have set up xorg mostly correctly.. 'mostly' because there is no glx module in your xorg.conf (or even a module section!). I'm not sure whether I should tell you how to try to add that information or to tell you how to manually install another driver, or tell you to try installing another one from the repositories or what. 

Well, we shall start by trying to do it the right way..

Please do this in the terminal just in case.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Please try this stuff in the terminal now.. Just in case your ubuntu fails to boot to anything but the text mode, you can always boot into the live-cd to talk to us for a quick fix. This is the same procedure as you did earlier, just installing a different version..

sudo apt-get install nvidia-glx

Then reboot and try our little tests again to see if stuff is working right. If not, repeat the process, except use

sudo apt-get install nvidia-glx-new

and try our little tests earlier to see if direct rendering is working.. Please report back with your results. I hope one of the above works, because that would be much nicer to deal with.

---

### Post by snow_56767 on 2008-02-13
Hi,
   I did what you said to do, but every time I try to enable visual effects I need to install 
nvidia-glx-legacy. Then it doesn't work! I'm still confused. :confused:

---

### Post by snow_56767 on 2008-02-13
I think this is weird. I was just in the terminal thinking on how I could get compiz to work.
And for some reason I typed Xgl and I got
```
the program Xgl is not currentl installed. You can get it by typing
sudo apt-get install xserver-xgl
```
So I did and I rebooted my computer with Xgl installed. Then I typed the command
```
compiz
``` and I got
```
aborting and using fallback: /usr/bin/metacity
```
How do I fix this? :confused:

---

### Post by snow_56767 on 2008-02-14
Hi,
   I think I fixed my problem. I felt kinda dumb after I figured out my problem, I installed
   nvidia-legacy-kernel-source. The code is:
```
sudo apt-get install nvidia-legacy-kernel-source
``` 
I thinkl that is what fixed my problem I'm going to reboot and find out.
I'll be back :)

---

### Post by snow_56767 on 2008-02-14
:mrgreen: YES IT WORKS!  :mrgreen:
The nVidia kernel source was the key to success! But if it weren't for you guys, I would have never learned about compiz or all the commands you told me!!!!
THANKS!!!!!!!! :mrgreen:

---

### Post by sdrakulich on 2008-04-11
Hi, I have the gotten the same problem after I unsuccessfully tried to install Beryl Windows Manager. It messed everything up for me, my screen resolution, everything....my visual effects worked just fine before I installed this, and now I can't turn it on.

It says "Desktop effects could not be enabled

I mean, what's Ubuntu (besides the best OS out there) without visual effects?

Please Reply and thank you

---

