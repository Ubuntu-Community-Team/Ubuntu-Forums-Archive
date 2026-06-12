---
title: "Xgl/compiz working but without 3d rendering?? fglrx"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by bobbymcsteels on 2007-07-31
OK not sure if this is even in the right part of the forum so I apologise for that now:P

I am using an Ati x1650xt gpu, I have xserver-xorg-fglrx installed.

Anyway I have just gotten compiz working with xgl and its looking very slick, so that was one job down time to install cedega..... but cedega failed the glxgears test.
So i ran 
```
]mcsteels@sansleballs:~$ fglrxinfo | grep direct

```
which returns that there is no direct rendering enabled (a sure sign that 3d isn't working)

But wen i run glxgears i get
```
mcsteels@sansleballs:~$ glxgears 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
49322 frames in 5.0 seconds = 9846.053 FPS
48915 frames in 5.0 seconds = 9781.316 FPS
49118 frames in 5.0 seconds = 9806.251 FPS
```
which is way quicker than wen I didnt have fglrx installed, but this is down to Xgl.

Compiz is still working all cubed up and sexified but why dont i have 3d rendering??

Here's the graphics relevant parts of my xorg.conf

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
.
.
.
<clip> 
.
.
.
Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection
.
.
.
<clip>
.
.
.
Section "Device"
	Identifier	"Ati x1650xt"
	Driver		"fglrx"
#	BusID		"PCI:4:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

glxinfo also tell me that XFREE-DRI isn't enabled, but it is in the xorg.conf so I cannot see where else to put it.


Thanx in advanced :guitar:

---

### Post by Steveway on 2007-07-31
You have no direct rendering because XGL "steals" all your direct rendering.
I'm not gonna explain this again, search around and you'll find out why.

---

### Post by bobbymcsteels on 2007-07-31
Ok I understand that and when i log in to a normal gnome session 3d rendering is working fine and dandy. So does it mean that 3d rendering is actually working in xgl therefore I can use 3d apps(games etc.) or because xgl is using my direct rendering makes it impossible?

BTW the reason I am asking these questions is because I don't know the answers and have searched for what I can and with no answers to my problem. I have been at this problem most of the day before finally making a post on here so it is not like I haven't tried to find a solution on my own, but when you dont exactly know what it is your looking for
> You have no direct rendering because XGL "steals" all your direct rendering.
I'm not gonna explain this again, search around and you'll find out why. 
doesn't really help me out much. Where as I appreciate any reply and help I get from anyone on this forum with more knowledge than me of my problem's. Pointing me in the right direction would have been the best thing you could have done if you didn't want to write a whole explaination or even not posted at all and let some one else answer the question who remembers when they had this problem/question and not knowing the answer..... instead of saying I'm not helping you out.
Thanx anyway tho

---

### Post by RAOF on 2007-07-31
> **bobbymcsteels said:**
> ...
which returns that there is no direct rendering enabled (a sure sign that 3d isn't working)
...
This is incorrect. "Direct rendering = no" is not the same as "3D acceleration = no".  "Direct rendering" is whether or not an application can talk directly to an OpenGL provider without going through the X server.  This can fail in two ways: (1) You don't have an OpenGL provider (your drivers are broken), or (2) You need to go through the X server to get OpenGL (you're using Xgl, you don't have DRI loaded, your drivers don't support DRI, etc).  Obviously, the latter is the case for you - this is slightly slower (there's some overhead involved in going through X), but it's still hardware accelerated.  

You do have 3D acceleration in Xgl.  Xgl doesn't work without it.

---

### Post by rellonaut on 2008-01-23
Hey, I had this same problem.  Yes XGL sort steals the direct rendering. but also know that it runs on a certain display (usually shows up as display 1 or something) So if XGL is that transparent layer using the directing rendering on display 1 then you might have dierct rendering on display 0. display 0 has no XGL or anything else but I've had direct rendering in the layer. to check run:

```
DISPLAY=:0 glxinfo | grep direct
```

hopefully this says yes. if so you can run any program you want I believe. I've run many games this way, I had to run them this way.  I know that I lacked window functionality in the display (i guess gtk and nautilus aren't running here)

There is an alternative.  Go to [http://ati.amd.com/]("http://ati.amd.com/") if you have an ati card and get the driver for linux. then build the package to your distro. then uninstall XGL you won't need it after the driver install depending on your card. :)

---

### Post by stoer on 2008-01-25
> **rellonaut said:**
> Hey, I had this same problem.  Yes XGL sort steals the direct rendering. but also know that it runs on a certain display (usually shows up as display 1 or something) So if XGL is that transparent layer using the directing rendering on display 1 then you might have dierct rendering on display 0. display 0 has no XGL or anything else but I've had direct rendering in the layer. to check run:

```
DISPLAY=:0 glxinfo | grep direct
```

hopefully this says yes. if so you can run any program you want I believe. I've run many games this way, I had to run them this way.  I know that I lacked window functionality in the display (i guess gtk and nautilus aren't running here)

There is an alternative.  Go to [http://ati.amd.com/]("http://ati.amd.com/") if you have an ati card and get the driver for linux. then build the package to your distro. then uninstall XGL you won't need it after the driver install depending on your card. :)

Sorry to crash into this thread,
I'm in the same boat as the poster.  Compiz and all effects work, i just can't play any 3d games.
DISPLAY=:0 glxinfo | grep direct = yes
So i can play 3d games....? but how
eg
Warsow says the following when i try to start it.
your openGL installation doesn't support direct rendering....you need the proprietary drivers.

How do you work around this please?

---

