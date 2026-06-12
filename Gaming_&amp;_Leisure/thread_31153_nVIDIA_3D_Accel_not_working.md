---
title: "nVIDIA 3D Accel not working"
date: 2005-05-02
forum: Gaming &amp; Leisure
---

### Post by stardotstar on 2005-05-02
I have got the nVIDIA drivers loaded and X is running properly.  I get the nVIDIA splash when X Starts.

I thought about how I'd test if the 3D Hardware Acceleration was working and apt-got Tuxracer to see if it displayed smooth and fast or jaggie and jerky.  

It is jaggie and jerkie - what do I need to do/know about how to get my G-Force 6600 to work with apps in general?

Hope for some kind pointers,

TIA Will.*

---

### Post by moopere on 2005-05-02
[QUOTE=stardotstar]I have got the nVIDIA drivers loaded and X is running properly.  I get the nVIDIA splash when X Starts.
[/QUOTE]

If you get the Nvidia splash screen then the driver is loading - you already have 3D accelleration(!).

To prove it, turn off the driver:

nvidia-glx-config disable

run glxgears and let us know the FPS it reports (not a good benchmark tool this, but its a reasonable indicator).  You'll prolly end up with something <500FPS

Now turn the driver back on

nvidia-glx-config enable

run glxgears again.  This time you'll see FPS >3000 (some folks report 10K+!)

Regards,
Craig

---

### Post by rdwtux on 2005-05-02
glxinfo cmd should tell you whether you are running 3d mode or not - right near the top.

I think something like "glxinfo | grep 3d" will work to see.

---

### Post by fubarpa on 2005-05-04
[QUOTE=rdwtux]glxinfo cmd should tell you whether you are running 3d mode or not - right near the top.

I think something like "glxinfo | grep 3d" will work to see.[/QUOTE]

I think you mean ```
glxinfo | grep direct
```

If the drivers are working correctly, you will see ```
Direct Rendering: Yes
``` .

---

### Post by Gags666 on 2005-05-04
> If the drivers are working correctly, you will see
```
Direct Rendering: Yes
```

AFAIK nVidia cards don't have DRI support that's why you have to uncomment the line which contains *load "dri"* in the xorg.conf. Even if you can see *Direct Rendering: Yes* you might not have 3d acceleration because nVidia's 3d acceleration works another way. For a correct installation of nVidia drivers you have to see *Direct Rendering: No*. But like I said - AFAIK. :)

---

### Post by gil-galad on 2005-05-04
[QUOTE=Gags666] you might not have 3d acceleration because nVidia's 3d acceleration works another way. For a correct installation of nVidia drivers you have to see *Direct Rendering: No*. But like I said - AFAIK. :)[/QUOTE]

Actually, it should say yes.   :)

---

### Post by graabein on 2005-05-05
Hi. I can't get glx to work either. glxinfo | grep render gives me:

```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

 ](*,) 

My xorg.conf says:
```
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	#Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
	Option		"RenderAccel" 		"true"
EndSection
```

I'm using Hoary with GeForce6600GT.

---

### Post by stardotstar on 2005-05-08
Still got problems getting Hardware rendering going.

I have tried:

```

wparker@monitor:/var/log $ glxinfo | grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

```

and find that my Xorg.conf is like this:

```

Section "Module"
        Load    "GLcore"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "speedo"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
        Load    "xtt"
EndSection

...

Section "Device"
        Identifier      "NVIDIA Corporation NVIDIA Default Card"
        Driver          "nvidia"
#       Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSectionSection "Monitor"
        Identifier      "BenQ FP737s-"
        HorizSync       31-83
        VertRefresh     56-76
        Option          "DPMS"
EndSection

...

Section "DRI"
        Mode    0666
EndSection

```

I have left out sections that I think are not relevant...

My logs tell me:

```

wparker@monitor:/var/log $ tail Xorg.0.log
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(**) NVIDIA(0): DPMS enabled
(EE) NVIDIA(0): Failed to load GLX
(==) RandR enabled
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element unix/:7100, removing from list!
Could not init font path element /usr/lib/X11/fonts/Speedo, removing from list!

```

```

wparker@monitor:/var/log $ tail XFree86.0.log
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!

```

and glxgears runs but obviously not in hardware rendering mode.

When my X session initialises I also get an obscure error too "Command did not run" or something like this.

Can anyone point me in the right direction for the GeForce 6600 please?

Will

---

### Post by stardotstar on 2005-05-08
sudo apt-get install nvidia-glx solved this one.

after doing the install I performed flxinfo | grep direct - the X session blinked out - logged me off and when I relogged in I found that it was all working.

BTW there does not seem to be any changes to my /etc/X11/xorg.conf file

Thanks.
Will

---

### Post by Professor X on 2005-05-08
You should comment out the Load "dri" and Load "glcore" lines in your /etc/X11/xorg.conf.  They are causing a conflict with the nvidia driver.

---

### Post by Snipersnest on 2005-11-24
[quote=stardotstar]sudo apt-get install nvidia-glx solved this one.

after doing the install I performed flxinfo | grep direct - the X session blinked out - logged me off and when I relogged in I found that it was all working.

BTW there does not seem to be any changes to my /etc/X11/xorg.conf file

Thanks.
Will[/quote]

I tried doing just about everything in this post...and my Cedega still fails the 3D Accell test... My GLxGears shows 14000 fps ...but most of my 3D games still lag. What else can I do?

---

### Post by wobster on 2005-11-25
Same here. I get the NVidia logo, and glxgears run quite fast. Still, I get unacceptable CPU load. 
I should mention that I recently upgraded from hoary to breezy. A self-written opengl application had 0% impact on the cpu before. it now has ~8%, even when I don't "move" any objects and such - that is, this seems to be the "idle-load". that is totally unacceptable ...

---

### Post by louisgag on 2005-12-14
Same here,

I tried all this thread's suggestions:

 I tried to run

apt-get ... glx..

then

enable config..

and then comment dri & glcore

and I still get glxgears to run 150fps ans use 100% CPU...


... :(

---

### Post by louisgag on 2005-12-14
...And I installed easyubuntu... nothing helped

I did what it said there: [http://www.ubuntulinux.org/support/documentation/faq/Official_nVidia](http://www.ubuntulinux.org/support/documentation/faq/Official_nVidia)

and couldn't complete this:

>>>   cd /path/to/nvidia/installer

>>>   sudo sh NVidia-Linux-x86-1.0-xxxx-yyyy.run

so I simply reinstalled using >>> apt-get install nvidia-glx nvidia-kernel-source nvidia common

and the same for the xorg servers...

and rebooted, 

result:

> 
5146 frames in 5.0 seconds = 1029.143 FPS
4958 frames in 5.0 seconds = 991.487 FPS
5184 frames in 5.0 seconds = 1036.785 FPS
5278 frames in 5.0 seconds = 1055.594 FPS
3644 frames in 5.0 seconds = 728.675 FPS
52 frames in 5.1 seconds = 10.244 FPS
50 frames in 5.0 seconds =  9.914 FPS
126 frames in 5.0 seconds = 25.068 FPS
131 frames in 5.0 seconds = 26.141 FPS
839 frames in 5.1 seconds = 165.116 FPS
6226 frames in 5.0 seconds = 1244.987 FPS
5635 frames in 5.2 seconds = 1089.201 FPS
2011 frames in 5.1 seconds = 393.445 FPS
590 frames in 5.0 seconds = 117.994 FPS
6193 frames in 5.0 seconds = 1233.972 FPS
5183 frames in 5.0 seconds = 1036.593 FPS
5746 frames in 5.0 seconds = 1149.147 FPS
4157 frames in 5.0 seconds = 831.396 FPS
2593 frames in 5.0 seconds = 518.592 FPS



when it's slow, I was performing other CPU demanding operations.

So, some improuvement...  :)

---

