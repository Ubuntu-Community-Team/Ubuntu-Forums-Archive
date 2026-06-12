---
title: "using compiz-settings-mangager to speed up unity/compiz"
date: 2013-04-30
forum: Desktop Environments
---

### Post by alpage2 on 2013-04-30
I have installed ubuntu 13.04 on an old desktop PC, AMD2800+ CPU and 1Gb RAM, and a GeForce FX5200 graphics card which is incompatible with nouveaux. After blacklisting nouveaux, the graphics is working, but with all the compiz animations turned on by default, it is grindingly slow for windows and menus to open and close by slow degrees!!

I'd like to use the compiz-settings-mangager to try to speed up the desktop by turning off all the animations and other special graphics effects, but when I open compiz-settings-mangager, it displays a warning that the wrong combination of settings can cause the desktop to become unusable, so I'd be grateful if anyone can specify what settings will maximise speed without trashing the desktop.

Thanks in anticipation.

---

### Post by stinkeye on 2013-05-01
I think you may have trouble running unity/compiz no matter what you do, with only 1mb of ram.
I regularly use over 1mb of ram with a few browser tabs open.
Should be able to buy some cheap ram.

Also check what gfx driver is running...
```
lspci -k | grep -A3 VGA
```

and unity support test...
```
/usr/lib/nux/unity_support_test -p
```
eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **lspci -k | grep -A3 VGA**
01:00.0 VGA compatible controller: NVIDIA Corporation GF116 [GeForce GTX 550 Ti] (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd Device 351a
	[COLOR="#FF0000"]Kernel driver in use: nouveau[/COLOR]
```
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   nouveau
OpenGL renderer string: Gallium 0.4 on NVCF
OpenGL version string:  3.0 Mesa 9.1.1

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
```

Can also try running the gnome-classic desktop which uses metacity as the window manager.
```
sudo apt-get install gnome-panel
```
and choose Gnome-classic(no-effects) at the login screen.

---

### Post by alpage2 on 2013-05-01
Many thanks for the details and example output - here is what I got on this machine:

```

alan@amd2800:~$ lspci -k | grep -A3 VGA
01:00.0 VGA compatible controller: NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1)
02:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: LeadTek Research Inc. WinFast TV 2000
	Kernel driver in use: bttv
alan@amd2800:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)
OpenGL version string:  2.1 Mesa 9.1.1

Not software rendered:    no
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

```

Does anything suggest itself?

Otherwise, I'll be happy to return to the gnome interface - many thanks for the code for that, also.

Regards
Alan

---

### Post by grahammechanical on 2013-05-01
A warning is just that, a warning. It was put there because so many people messed around with the settings and then complained that Ubuntu somehow, all on its own, broke itself. You will notice that we can no longer disable the Ubuntu Unity Plugin. It is for the same reason. People disabled that plugin and then the next time they rebooted discovered that they had wallpaper but no top panel or launcher.

You can accept the warning and record what you do. Then if something breaks you know what you have to undo. Do not do too many changes at once. Do one change at a time and see whether something breaks.

It could be that your hardware is not capable of running Unity 3D. In which case you are running Unity on something called llvmpipe. Back in the days of 12.04 if the hardware was under powered we got Unity 2D installed. We could even install Unity 2D as an alternative desktop that would work if something broke Compiz because it used a different window compositor. But Unity 2D is no longer available and machines with lower specification hardware use llvmpipe in an attempt to reproduce Unity 3D on such low specified hardware.

It could be that the graphic adapter is just not up to task, even with llvmpipe.

Regards.

---

### Post by stinkeye on 2013-05-01
Your graphics are being software rendered (llvm)which is why it's sluggish.
My nvidia card (GeForce GTX 550 Ti) runs fine with the nouveau driver.
Not sure of the current state of your card with the nvidia drivers in 13.04 and find it hard 
to find info if any nvidia driver works at all with your card.

That's the issue anyway ...and hopefully someone who knows more than I, can help.

---

### Post by alpage2 on 2013-05-01
Hi All

Many thanks to both responders for the help and advice. At least I have a better understanding of the nature of the problem, now.

I turned off:

animations
fading windows
enhanced zoom desktop
copy to texture

with the compiz manager, and it was the last one, possibly in combination with one or more of the above, that provided the most benefit - windows now minimise or close instantly rather than very slooowwwwllyy!!

But overall, it seems clear that I don't have the resources to run unity with this old graphics card (it runs fine on a 1Gb Acer netbook), so when I have a bit of time, I'll convert to the gnome desktop, and for future versions it will be gnome, or even xubuntu  ;)

Thanks again
Alan

---

### Post by MichalVlasak on 2013-06-01
Please, how do you install ubuntu 13.04? When I installed it black screen appeared. I installed nvidia-173xx but nothing changes.

---

### Post by bjbraams2 on 2014-04-20
Thank you stinkeye. Your advice to run the gnome-classic desktop with metacity was useful to me a year after your post, now in connection with 14.04 LTS. Reference: [http://askubuntu.com/questions/450555/very-slow-graphics-performance-after-upgrade-12-04-14-04](http://askubuntu.com/questions/450555/very-slow-graphics-performance-after-upgrade-12-04-14-04)

---

