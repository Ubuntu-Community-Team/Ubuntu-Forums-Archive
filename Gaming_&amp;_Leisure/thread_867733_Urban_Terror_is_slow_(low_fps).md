---
title: "Urban Terror is slow (low fps)"
date: 2008-07-23
forum: Gaming &amp; Leisure
---

### Post by OnlyWhisky on 2008-07-23
I have kubuntu 8.04.1 with kde4.1rc1.

My hardware: 
Celeron2800, 1024MB RAM, AGP8 NVidia GeForce 6800GT 256MB.
driver is: nvdidia, 173.14.09
in xorg.cfg nvagp is set to 8.

In Urban Terror I have low fps when playing with opponents, when shooting and with snow effects, etc. Fps sometime down to 8-20. In normal case (no  other players and now effects) it is 85 (maxfps).

I have tried different video settings with no success. What could it be?

---

### Post by lesergi on 2008-07-23
Can you post the ouput of glxgears?

Bye!

---

### Post by OnlyWhisky on 2008-07-23
Here it is.
$ glxgears
6942 frames in 5.0 seconds = 1388.316 FPS
7225 frames in 5.0 seconds = 1444.939 FPS
6122 frames in 5.0 seconds = 1220.387 FPS
5284 frames in 5.0 seconds = 1056.730 FPS
7416 frames in 5.0 seconds = 1483.059 FPS
7387 frames in 5.0 seconds = 1477.327 FPS
7374 frames in 5.0 seconds = 1474.669 FPS
7358 frames in 5.0 seconds = 1471.464 FPS
Also 
$ glxinfo | grep direct
direct rendering: Yes
$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6800 GS/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 173.14.09
OpenGL extensions:

---

### Post by lesergi on 2008-07-23
Mmmm... I have also falls of fps, but 8-20 fps is too slow...

Try to install nvidia-glx-envy driver, maybe it could be a version problem.

Bye!

---

### Post by OnlyWhisky on 2008-07-23
I am using nvidia-glx-envy. Seems like game problem, probably. I will try other game.

---

### Post by OnlyWhisky on 2008-07-24
I have the same expirience with nexus.
May be reason is that I have installed kubuntu as hardy heron when it was beta and then just updated it? I don't want to reinstall kubuntu. How can I find out what is the problem with games (and not only) in my system?

May be old version of nvidia drivers should be better?

---

### Post by nikau on 2008-08-04
Hi, 
I experienced having low fps in various games in Ubuntu eg. ETQW, UrbanTerror etc. and I thought I had a graphic card issue! I own an AMD Athlon 2500+ CPU, a Radeon HD2600pro AGP GPU (512Mb)and have 1gig of RAM. In the beginning this system lagged in all my games and I started playing with xorg.conf and did all the GPU related tweaking that I could come up with.. to no avail! 
I noticed that that ETQW only used 128Mb of my GPS vRam (fix: ./etqw +set sys_VideoRam 512). This didn't give me higher fps but allowed me to get a better resolution (yay!!). After some tweaking I decided to try something different. I clocked my CPU from 2500+@3200+ setting FSB=200mHz, multiplier=11x and vCore=1.7. This dramatically improved my gaming experience and glxgears gives ~4000fps vs ~3500fps before the clock! So my conclusion is that I didn't have a GPU problem after all.. but rather my CPU was the bottleneck... Your specs are pretty close to mine but I think your Celeron CPU is your main problem.. I don't know this for a fact but thats my guess!

My system:
[LIST]
X@X:~$ cat /proc/cpuinfo[/LIST]
[INDENT]processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 3200+
stepping        : 0
cpu MHz         : 2205.057
cache size      : 512 KB[/INDENT]

[LIST]
X@yX:~$ cat /proc/meminfo[/LIST]
[INDENT]MemTotal:      1035864 kB[/INDENT]

[LIST]
X@yX:~$ fglrxinfo[/LIST]
[INDENT]display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 Pro AGP
OpenGL version string: 2.1.7769 Release[/INDENT]

[LIST]
X@X:~$ uname -r[/LIST]
[INDENT]2.6.24.7-rt[/INDENT]

//As I have shown here, glxgears doesn't depend on the GPU alone, The CPU
//and RAM are also important. The output of glxgears can be used to
//estimate the effects of single changes to a system..
[LIST]
X@X:~$ glxgears[/LIST]
[INDENT]19727 frames in 5.0 seconds = 3945.310 FPS
17441 frames in 5.0 seconds = 3488.088 FPS
19616 frames in 5.0 seconds = 3923.041 FPS
19595 frames in 5.0 seconds = 3918.874 FPS
19639 frames in 5.0 seconds = 3927.600 FPS
19472 frames in 5.0 seconds = 3894.225 FPS
19778 frames in 5.0 seconds = 3955.545 FPS
19625 frames in 5.0 seconds = 3924.856 FPS
19452 frames in 5.0 seconds = 3890.292 FPS[/INDENT]

---

### Post by uberlube on 2008-08-04
Your problem....you own AMD graphics cards.


Your solution.... get NVIDIA. :)

---

### Post by nikau on 2008-08-04
> **uberlube said:**
> Your problem....you own AMD graphics cards.


Your solution.... get NVIDIA. :)

:) ... Yeah I get that allot, but replacing my ATI card with eg. a Nvidia 8500GT gives me about the same performance in ETQW on my system. (ioUT however seems to be more sensitive to GPU brand). Actually it is my personal opinion that ATI cards are not too bad.. That said, the main purpose of my PC is not gaming, but presentations and video playback which ATI is better suited for.. 

I Haven't been able to find any faithful benchmarks that actually compare these to cards so you'll have to take my word for it (or test it yourself)

---

### Post by Zero Prime on 2008-09-06
There is nothing wrong with AMD/ATI.  I have integrated ATI graphics and get 92FPS with Compiz on and 99FPS with Compiz off (that's with the FPS limiter on). 
I'm also using the 2.6.24-21-generic kernel.  It seems to work a lot better with ATI cards.

---

### Post by Ansraliant on 2009-02-02
Nikau, I have a similar problem with my ATI Radeon 2600.
Here's some information about my pc

```

cat /proc/cpuinfo
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: Intel(R) Pentium(R) 4 CPU 2.80GHz
stepping	: 9
cpu MHz		: 2813.506
cache size	: 512 KB

```

```

cat /proc/meminfo
MemTotal:      3112180 kB

```

```

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 Pro AGP
OpenGL version string: 2.1.8304 Release

```

```

glxgears (cmpiz disable)
6524 frames in 5.0 seconds = 1304.385 FPS
5232 frames in 5.0 seconds = 1046.240 FPS
4970 frames in 5.0 seconds = 993.851 FPS
6330 frames in 5.0 seconds = 1265.908 FPS
6683 frames in 5.0 seconds = 1335.931 FPS

```

As you can see, I have the same video card as you, and almost the same processor. But my fps are really low :shock:, they should be around 4000.
That's why i want to ask you what should I do to make the fps go to 4000.
I hope you can help me.
Here's my xorg.conf:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "Viewsonic"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Radeon 2600"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Radeon 2600"
	Monitor    "Viewsonic"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1680x1050" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

---

