---
title: "Nvidia Question..."
date: 2005-08-04
forum: Gaming &amp; Leisure
---

### Post by grofaz on 2005-08-04
...how do you know if your cards 3D Acceleration is on or not ? Is there a way to check ??

---

### Post by Mishura on 2005-08-04
The easiest way, is to restart X (CTRL + ALT + BACKSPACE) and if the Nvidia Splash screen (A white screen with the nvidia logo on it) appears for a second before hitting GDM/KDM, that means you are 3D accelerated.

There is much easier unix-y ways of checking.. but I can't remember them..

---

### Post by grofaz on 2005-08-04
So if I see the nvidia logo screen during boot up 3D Acceleration is working ??

---

### Post by Sunil on 2005-08-04
just open up a terminal and type glxgears and check the frame rate, anything above 800 is good

---

### Post by Mishura on 2005-08-04
> So if I see the nvidia logo screen during boot up 3D Acceleration is working ?? 

Should be.  I can't see why not.   I know that everytime I see the splash, I know that my nVidia stuff is working.

> just open up a terminal and type glxgears and check the frame rate, anything above 800 is good

Kind of.  To get a real reading with GlxGears, resize the gears window as large as you can while still seeing some of your terminal.  At that size, you'll start to get glxgears readings that look more realistic.. (You'll never see above 150 fps on a game now will you?)

Lets see... there was supposed to be a way to check using the "cat" command and your sys or proc directory...

Doing a "cat /proc/modules | grep nvidia" gave me:

```
nvidia 3923452 24 - Live 0xf17e2000
agpgart 33608 2 nvidia,intel_agp, Live 0xf1080000
``` 

Which looks about right.  Nvidia module is loaded, meaning that its using the 3D accellerated drivers, and agpgart is loaded as well..  which is *I THINK* the kernel driver for AGP.  

There is, of course a much more cleaner way of checking.. but the way it goes is:  If "nvidia" driver module is loaded, and you see a Nvidia boot splash when starting X, and get a much higher fps in glxgears.. then you are probably good to go.  Final test, download a 3D game like Enemy Territory or Nexuiz and give that a go.  If it plays with anything above 1 fps, then you are good.

---

### Post by grofaz on 2005-08-05
Thanks for the replies, I appreciate it.

---

### Post by c-m on 2005-08-09
i used to see the nvidia logo on boot, when i used Yoper, I have just installed ubuntu and the logo doesn't appear. To top it off i get around 240fps on gears (small) and only about 30fps with them enlagred.

Does ubuntu no come with the nvidia driver by default? How do i go about setting it up?

---

### Post by grofaz on 2005-08-10
Use synaptic to install nvidia driver and nvidia-settings, or apt-get.

---

### Post by c-m on 2005-08-10
[QUOTE=grofaz]Use synaptic to install nvidia driver and nvidia-settings, or apt-get.[/QUOTE]
 i have nvidia-glx, nvidia-settings and nvidia-kernel-common Is there anything else i need to install from synaptic?

---

### Post by Lord Illidan on 2005-08-10
Is the driver in /etc/X11/xorg.conf "nvidia"?

---

### Post by c-m on 2005-08-10
[QUOTE=Lord Illidan]Is the driver in /etc/X11/xorg.conf "nvidia"?[/QUOTE]
 no its "nv"

> 
Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
	Option "TwinView" "true"
	Option "TwinViewOrientation" "Clone"
	Option "TVOutFormat" "COMPOSITE"
	Option "TVStandard" "PAL-G"
	Option "SecondMonitorHorizSync" "30-50"
	Option "SecondMonitorVertRefresh" "60"
	Option "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480;    512x384,512x384"
EndSection




---

### Post by Lord Illidan on 2005-08-10
Change it to nvidia, then..and restart and experience open gl support!

---

### Post by c-m on 2005-08-10
worked a treat cheers.

---

### Post by c-m on 2005-08-13
[QUOTE=c-m]worked a treat cheers.[/QUOTE]
 
how do i get the nvidia driver to work with a new kernel.

everything works fine with the defualt ubuntu 386 kernel, but if i use synaptic to get the -k7 kernel or even if i compile my own, X will not start. X complains that the nvidia module cannot be loaded, and as a result i have to change my xorg.conf back to "nv" rather than "nvidia".

---

### Post by grofaz on 2005-08-13
Here's another nvidia question for you. I just installed a new 6800 GT card. I uninstalled nvidia-glx etc. and reinstalled after installing my new card. How come my xorg.conf file still reflects my old card ? Do I need to update that file somehow ? Or can I safely leave it alone. My new card seems to be working. I went from 900 fps to 12000+ fps. Cool!

It just bugs me that it lists the old FX 5700 XT card and not the new puppy.

---

### Post by Ubunted on 2005-08-13
[QUOTE=c-m]how do i get the nvidia driver to work with a new kernel.

everything works fine with the defualt ubuntu 386 kernel, but if i use synaptic to get the -k7 kernel or even if i compile my own, X will not start. X complains that the nvidia module cannot be loaded, and as a result i have to change my xorg.conf back to "nv" rather than "nvidia".[/QUOTE]
 I just now installed the k7 kernel via Synaptic, rebooted into it, removed the 386, rebooted again and all was fine. I had that error when I tried to remove the 386 and install the k7 at the same time.

---

