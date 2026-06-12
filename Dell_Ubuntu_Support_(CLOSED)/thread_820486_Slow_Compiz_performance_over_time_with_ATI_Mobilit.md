---
title: "Slow Compiz performance over time with ATI Mobility x1400"
date: 2008-06-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Mega_Mike on 2008-06-06
In Hardy, after running my Inspiron 6400 (E1505) for over a few hours and letting the screen saver kick in occasionally, compiz slows my computer to a crawl.  Sometimes it gets so bad that it actually freezes and pressing ctrl+alt+f1 to get to a command prompt or alt+prntscrn+b won't reboot.

While my performance is slow, top shows nothing hogging my cpu.  I know a couple other hardy users with the same issue.  The only solution so far is to reboot.  

My graphics card is an ATI Mobility x1400.  I am using the fglrx drivers without XGL.

---

### Post by SierraComp on 2008-06-07
I am experiencing the same problem. I also have a Inspiron 6400. I have not been able to find a solution yet.

---

### Post by ksorg on 2008-06-07
I have Dell Inspiron 6400 with T7200 CPU and Ati x1400. So I'm working on Ubuntu 8.04 and running compiz. I've no problems with it. It works very fast and stable.

---

### Post by SierraComp on 2008-06-09
I switched back to the original kernel and the problems seems to have gone away. I think the problems started after an update.

I will report back after I test it for a few more days with the old kernel to make sure.

---

### Post by Mega_Mike on 2008-06-16
Yeah I am running the latest Hardy Kernel 2.6.24-18.  I haven't tried running an earlier kernel yet.  btw, I never had this issue in Feisty or Gutsy.  Its a really odd problem that only occurs after using the system for a while.  I used to think it was due to the screensaver and I edited **/etc/default/acpi-support** and changed the following variables:
[B]ACPI_SLEEP_MODE=standby
SAVE_VBE_STATE=false
POST_VIDEO=false[/B]

So far...I'm not sure its making any difference (got all these recommendations from the unofficial AMD ATI wiki).  Plus this is my xorg.conf file.

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier  "ATI Radeon Mobility x1400"
	Driver      "fglrx"
	VendorName  "ATI"
	BoardName   "ATI Radeon (fglrx)"
	Option	    "DRI" "true"
	Option	    "XAANoOffscreenPixmaps" "true"
	Option	    "TexturedVideo" "on"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	### Experimental 
        Option      "Textured2D" "on"
        #Option      "TexturedXRender" "on"
        #Option      "BackingStore" "on"
	BusID       "PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	DisplaySize  410	310
	Option	    "DPMS" "true"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"ATI Radeon Mobility x1400"
	Defaultdepth	24
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "Extensions"
	## For Textured2d and Textured XRender
        Option      	"RENDER" "On"
	Option		"Composite"	"On"
	Option		"XVideo"	"On"
EndSection

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	#Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

---

### Post by Mega_Mike on 2008-06-16
Another thing I just thought of is that I am running Eclipse and JBoss with JDK 1.6u6 for extended periods of time as well.  It could be something with the Java environment as well.....again top is not showing anything.

---

### Post by Mega_Mike on 2008-06-17
Correction.  I don't think I runaway JDK has anything to do with it.  I ran all day without eclipse and the same problem occurred.

I read elsewhere that the problem is linked to a big in the power management service HAL.  I went and did a 
sudo /etc/init.d/hal restart

that sort of worked....the system is response but some of the compiz effects are still jerky.

---

### Post by SierraComp on 2008-06-18
I ran an older version of the kernel without any problems. Today I installed the latest updates, and the kernel updated to Kernel 2.6.24-19. So far no problems.

---

### Post by Mega_Mike on 2008-06-26
Whats driving me nuts is that this problem is not consistent.  It happens the majority of the time I am using my laptop for over several hours, but not ALL the time.  

One of the symptoms is that when the computer is slow it seems like system monitor is eating up all my cpu resources has it spikes to 60% usage.  Now I read that this is a bug as well, but I have not seen a solution.

Some speculate that this is due to faulty ATI proprietary drivers (using the Hardy 8.47.3 version).  That I can believe.  I am just hoping to find a workaround for now [img]http://ubuntuforums.org/images/smilies/icon_sad.gif[/img]


Oh and by the way, this right here is just painful.  Intel video is supported in Linux before ATI...wow, this sux.
[http://linux.dell.com/wiki/index.php/Tech/Video](http://linux.dell.com/wiki/index.php/Tech/Video)

---

### Post by Mega_Mike on 2008-07-02
Ok.  I think I solved my issue.  I manually upgraded the catalyst driver from 8.47 to the latest 8.6 by following the instructions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")

I also added 

Option "UseFastTLS" "2"

in the **Section "Device"** or my /etc/X11/xorg.conf.  Supposedly that option works to prevent x lockups when using wine (which I use regularly).

So far performance has been fine and I have been running my laptop now for quite a while.  The only issue is see is when I do
**sudo glxinfo | grep rendering**

I used to get a response of **Yes** with 8.47, now my response is 
**direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)**

Not sure if one or both of the above fixed the issue.  But so far so good.  I still have my fingers crossed [-o<

---

### Post by misterhead on 2008-07-03
> **Mega_Mike said:**
> Ok.  I think I solved my issue.  I manually upgraded the catalyst driver from 8.47 to the latest 8.6 by following the instructions here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")
 [-o<

Yes, I too installed this driver for my x600 and it seems to have solved this same issue for me.

---

### Post by Mega_Mike on 2008-07-21
Unfortunately the new drivers didn't fix my issue :(

Its now extremely consistent.  Every single day after roughly 6 hours of usage my X server performance takes a huge hit.  I cannot restart the X server (/etc/init.d/gdm stop..then start) without it locking up the entire machine.  The only thing I can do is reboot my Inspiron 6400 as soon as the lag kicks in.

---

### Post by Paul S on 2008-08-02
> **Mega_Mike said:**
> Unfortunately the new drivers didn't fix my issue :(

Its now extremely consistent.  Every single day after roughly 6 hours of usage my X server performance takes a huge hit.  I cannot restart the X server (/etc/init.d/gdm stop..then start) without it locking up the entire machine.  The only thing I can do is reboot my Inspiron 6400 as soon as the lag kicks in.

Have you tried the open source driver "ati" or "radeonhd"?  If you need 3D, they won't work.  If you need tv out, they won't work.

There is an experimental version of the latest developed radeon "ati" driver, available from xorg-pushers.  I'm using it with an X1400 E1505 on hardy and it does everything except tv out.  3D and compiz are faster than fglrx, and suspend works too.  This is a possible alternative to consider to fglrx.  See:

[http://www.phoronix.com/forums/showthread.php?t=9951](http://www.phoronix.com/forums/showthread.php?t=9951)
[http://phoronix.com/forums/showthread.php?t=10181](http://phoronix.com/forums/showthread.php?t=10181)
[https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)

You can try it on a live CD to see if it suits your needs, then install it if it does.

regards,

---

### Post by danker on 2008-09-14
I have the same problem. Using X1600 Mobility on ASUS A7J with Gentoo and 8.8 Catalyst drivers. After sometime running heavier (3D?) programs. System performance drops in 3D programs. Also I believe there is overall system performance drop.

---

### Post by danker on 2008-09-14
I have the same problem. Using X1600 Mobility on ASUS A7J with Gentoo and 8.8 Catalyst drivers. After sometime running heavier (3D?) programs. System performance drops in 3D programs. Also I believe there is overall system performance drop.

---

