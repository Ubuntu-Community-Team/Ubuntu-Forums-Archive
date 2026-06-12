---
title: "Xorg memory leak on intel"
date: 2009-07-07
forum: Desktop Environments
---

### Post by mehturt on 2009-07-07
I'm currently using Ubuntu 9.04 on x86_64 with E17 installed from SVN, the video hardware is GM965/GL960.

My problem is that the xserver consumes a huge amount of memory if my laptop is on for 1 day.  After the start, it consumes about 400M of virt memory, 50M of res memory (numbers come from 'top'), the next day it consumes more than 1.2GM of virt memory and 800M of res memory.

I have came across multiple memory leak bugs on launchpad, but they all involve compiz.  I'm not sure whether this problem is the same. I have compositing switched on.

For some time I was trying to use the packages from [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates/) and [https://edge.launchpad.net/~xorg-edgers](https://edge.launchpad.net/~xorg-edgers) but the problem did not go away even if various fixed were mentioned in the launchpad bugs as being commited.

My question is whether I should file a separate bug on launchpad or is this bug already existing in there.

Thanks..

---

### Post by mehturt on 2009-07-15
Somebody suggested the symptom is number of object increasing in /proc/dri/0/gem_objects, but it's not my case.
Right now, with Xorg running for 2 days, the consumption is:
17214 root      20   0 1436M 1026M 14676 S 11.0 51.9  1h14:23 /usr/bin/X -quiet -br -nolisten tcp vt7 :0

---

### Post by VCoolio on 2009-07-15
Maybe same problem here; after 16 hours 173 Mb memory usage by Xorg and counting. After appr. 40 hours everything is used (which is not much; 512 Mb + 512 Swap). Jaunty i686 with e17 from svn (including ecomorph). NVidea GeForce FX5200. 

xorg.conf:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option	"RenderAccel"	"true"
	Option	"AllowGLXWithComposite" "true"
	Option	"AddARGBVisuals" "True"
	Option	"AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor	"Configured Monitor"
	Device	"Configured Video Device"
EndSection

Section "Extensions"
	Option	"Composite" "Enable"
EndSection

Section "Module"
	Load	"glx"
EndSection

# Re-enable ctrl+alt+backsp = kill x and login screen
Section "ServerFlags"
        Option	"DontZap"	"false"
EndSection
```

Ideas on troubleshooting and solving are most welcome.

---

### Post by VCoolio on 2009-07-17
Following [this]("http://www.nvnews.net/vbulletin/showthread.php?t=118088") I added some stuff to xorg.conf:

```
# heuristic governs amount of pixelmap data that is moved to video memory, which is faster than RAM
# TripleBuffer enables more efficient method of double buffering (used to remove flicker from a screen update)
# pixmapcache and allowshmpixmaps set to 0 prevents applications from allocating Shared Memory pixmaps
Section "Device"
	Option	"MigrationHeuristic" "greedy" #Available values are: smart, greedy, always
	Option	"TripleBuffer"	"True"
	Option	"PixmapCacheSize" "1000000"
	Option	"AllowSHMPixmaps" "0"
EndSection
```

and to ~/.xinitrc:
```
#This command will enable X pixmaps to be placed in your GPU's video memory instead of the traditional system memory, allowing the NVIDIA X driver to optimally accelerate rendering operations involving such pixmaps.
nvidia-settings -a InitialPixmapPlacement=2
```

Don't know if it is really ok and which of the additions does the trick, but looking good. It seemed ok to move stuff from RAM to video memory, so maybe that was it.

---

### Post by mehturt on 2009-07-18
It seems you have nvidia, but I have intel..

---

### Post by VCoolio on 2009-07-18
I know, but first I thought it might have to do with e17 (may still be ...). But if not, sorry for interrupting.

---

### Post by ddrichardson on 2009-07-18
FYI anyone on KDE, setting MigrationHeuristic to greedy causes icon corruption.

---

### Post by ddrichardson on 2009-07-18
Meant to say, the memory leak has several factors and has a bug report here [http://is.gd/1Dfcb](http://is.gd/1Dfcb)

---

### Post by mehturt on 2009-07-18
> **VCoolio said:**
> I know, but first I thought it might have to do with e17 (may still be ...). But if not, sorry for interrupting.

no problem.. I thougt this bug is intel related..

---

### Post by mehturt on 2009-07-18
> **ddrichardson said:**
> Meant to say, the memory leak has several factors and has a bug report here [http://is.gd/1Dfcb](http://is.gd/1Dfcb)

the URL does not work

---

### Post by ddrichardson on 2009-07-18
Sorry is.gd doesn't seem to like "+": [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/98783](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/98783)

---

### Post by mehturt on 2009-07-18
Thanks for the link.  I have subscribed.

---

### Post by mehturt on 2009-07-21
It must be e17 then.  I am using ratpoison today the whole day and the memory usage of X did not go up.

---

### Post by James.Pandavan on 2009-07-26
I noticed that my xorg memory usage went up whenever I use [freemind]("http://freemind.sourceforge.net/wiki/index.php/Main_Page"). I had to restart the process to free up memory.

```

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
    Subsystem: AOPEN Inc. Device 063e
    Flags: bus master, fast devsel, latency 0, IRQ 2301
    Memory at fd900000 (64-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at ff00 [size=8]
    Capabilities: <access denied>
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
    Subsystem: AOPEN Inc. Device 063e
    Flags: bus master, fast devsel, latency 0
    Memory at fdc00000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

```

---

### Post by VCoolio on 2009-08-26
There is a bug in xorg that causes a memory leak with the way e17 draws the mouse. Read [this]("http://www.mail-archive.com/enlightenment-users@lists.sourceforge.net/msg12928.html"). Solution: in settings panel > look > mouse cursor, either change mouse to x cursor or disable idle cursor. Maybe it's not your issue, but I thought I'd mention it.

---

### Post by mehturt on 2009-08-27
Thanks for the information, I'll give it a try.  Even though I started to use ratpoison and I'm not sure I'll ever go back:lolflag:

---

### Post by mehturt on 2009-08-28
Looks much better now, thanks.  I subscribed to the Xorg bug as well.

---

### Post by ert45 on 2010-04-15
Hello,

The solution proposed in [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/186354](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/186354) worked for me: disable xinerama.

On ubuntu 9.04 (using an Intel GMA chipset), I added this at the bottom of my /etc/X11/xorg.conf and then had no more problem after restarting the X server:

Section "Serverflags"
    Option "Xinerama" "false"
Endsection

---

### Post by ert45 on 2010-04-15
Hello,

The solution proposed in [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/186354](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/186354) worked for me: disable xinerama.

On ubuntu 9.04 (using an Intel GMA chipset), I added this at the bottom of my /etc/X11/xorg.conf file and then had no more problem after restarting the X server:

Section "Serverflags"
    Option "Xinerama" "false"
Endsection

---

