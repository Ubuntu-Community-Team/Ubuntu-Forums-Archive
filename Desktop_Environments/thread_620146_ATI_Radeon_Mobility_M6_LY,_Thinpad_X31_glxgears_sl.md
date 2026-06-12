---
title: "ATI Radeon Mobility M6 LY, Thinpad X31: glxgears slow, windows borders problems"
date: 2007-11-22
forum: Desktop Environments
---

### Post by phen on 2007-11-22
Hello All!

Allthough Compiz works, there are problems left with my ATI card:

I use the "ati" driver and reduced the color depth as supposed in another post here in the forums.

I have no modules activated in xorg.conf

I have 2 problems:
glxgears reports only 300fps, and glxinfo reports
```

OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1

```

but compiz works good except problem 2:
when maximizing a window, its border turns white and the icons dissappear. :confused:

this is my xorg.conf:
```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"ati"
	Option          "XAANoOffscreenPixmaps"
EndSection

Section "ServerLayout"
	Option          "AIGLX" "true"
Endsection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```


HELP please! :)

---

### Post by xeth_delta on 2007-11-22
I would suggest to you to first back-up your current **xorg.conf** file, just in case something goes wrong while changing the configuration.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bkp
```

Then you can try using the **radeon** driver instead of the **ati**.

Let us know how it goes.
Xeth

---

### Post by Ice_cone on 2007-11-22
I'm using X31 too and having the same problem no.2: title bar turns white when maximized
I didn't install any graphics card drivers manually.  what driver am I using?
thanks

---

### Post by phen on 2007-11-23
xeth: using the radeon driver didn't help, i tried the following:

driver "ati" with the modules section
```
#Section Modules
#	Load	"dri"
#	Load	"extmod"
#	Load	"glx"
#	Load	"GLcore"
#EndSection
```

driver ati without modules section

same with driver "radeon"

Ice_cone: you can see wich driver You use in the file
/etc/X11/xorg.conf

```

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"ati"
        ...
EndSection
```

before working with your xorg.conf, you should make a backup, like xeth suggested!

still reading forums and trying but no progress here...

---

### Post by phen on 2007-11-25
bump!

---

### Post by xeth_delta on 2007-11-25
A couple of things to check. I suspect 3D acceleration is not enabled, post the output of:
```
glxinfo | grep direct
```

and 
```
lspci | grep -i graph
```

What happened when you tried to use the radeon driver? Did the X server just not start at all? What were the log messages?

---

### Post by phen on 2007-11-27
Hello,


```
kai@schlepptop:~$ glxinfo | grep direct
direct rendering: Yes

```

I suspect you want to see the graphics adapter entry:
```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
```

actually, i tried radeon, but never checked the speed of glxgears. The OpenGL part of glx info didn't change though.

Ill try....

---

### Post by phen on 2007-11-27
ok, tried the radeon driver. it didn't change anything:

glxgears is stuck between 350 to 400fps

```
kai@schlepptop:~$ glxinfo | grep direct
direct rendering: Yes

```


```
kai@schlepptop:~$ glxinfo | grep OpenGL
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI Radeon 20061018 AGP 4x x86/MMX/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.0.1
OpenGL extensions:

```


maybe i have to install something? I never installed any additional packages. I just edited my xorg.conf to enable rendering.

are any modules needed to add to xorg.conf?

Mesa is indirect rendering, right? why does it say direct rendering Yes, then?

compiz works ok, maybe a litlle slow, but since i dont use the eye-candy, only the usability-enhancing plugins, thats ok.

thanks for your help!

---

### Post by xeth_delta on 2007-11-27
It seems you actually have direct rendering enabled on your computer. From what I can see, your graphics card is an integrated one. These cards have relatively low performance when compared with a discrete solution.

My new laptop also has an integrated graphics card, intel 945GM. Direct acceleration works and glxgears gives me between 800-1000 fps. Now, I am not saying this is a certainty, but depending on how old your graphics card is, the performance you see might in fact be what it in fact can offer.

How old is your laptop? If I recall right the Radeon Mobility M6 is a design from a couple of years ago. I might be wrong, of course. Maybe someone with more knowledge on ATI cards can give you more information on it.

While using the **radeon** driver, did the same problems with the white borders and icons dissappearing persist?

Xeth

---

### Post by xeth_delta on 2007-11-27
Just checked with a friend that has a Thinkpad X31. He uses the radeon driver. 3D acceleration is enabled and gets for glxgears more or less the same values as you do.

---

### Post by phen on 2007-11-28
thanks for your help, xeth. I expected a little bit more, but its ok like it is :) but why is MESA written for OpenGL?

thats my last question!

cheers

---

### Post by xeth_delta on 2007-11-28
I am no expert on how graphics card drivers ar implemented in X.org, but let's try.
From [http://www.mesa3d.org/]("http://www.mesa3d.org/"):

> Mesa is an open-source implementation of the OpenGL specification - a system for rendering interactive 3D graphics. 

A variety of device drivers allows Mesa to be used in many different environments ranging from software emulation to complete hardware acceleration for modern GPUs. 

Mesa ties into several other open-source projects: the Direct Rendering Infrastructure and X.org to provide OpenGL support to users of X on Linux, FreeBSD and other operating systems.

From [http://dri.freedesktop.org/wiki/]("http://dri.freedesktop.org/wiki/"):

> The Direct Rendering Infrastructure, also known as the DRI, is a framework for allowing direct access to graphics hardware under the X Window System in a safe and efficient manner. It includes changes to the X server, to several client libraries, and to the kernel. The first major use for the DRI is to create fast OpenGL implementations. 

The DRI is an integral part of X.org 7.x, and integrates with Mesa, an open source implementation of the OpenGL API. Several 3D accelerated drivers have been written to the DRI specification, including drivers for chipsets produced by ATI, Matrox, 3DFX, and Intel..

So, it would seem that the part that provides hardware acceleration is DRI and it is integrated with mesa.

Quoting from another website:
> In computing, the Direct Rendering Infrastructure (DRI) is an interface and a free software implementation used in the X Window System to securely allow user applications to access the video hardware without requiring data to be passed (slowly) through the X server. Its primary application is to provide hardware acceleration of the Mesa implementation of OpenGL. It has also been adapted to provide OpenGL acceleration on a framebuffer console without an X Server running.

After issuing a glxinfo, look at the line describing the OpenGL renderer. Hardware acceleration provided by Mesa DRI and your graphics card, for example:

```
OpenGL renderer string: Mesa DRI Intel(R) 945GM 20061017 x86/MMX/SSE2
```

Hope this was useful.

---

### Post by Ice_cone on 2007-11-29
If I enabled xgl I get this results:
user@x31-laptop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

Even scrolling a webpage is now very slow

I got a yes if I remove xgl.
anyone can help me?
thanks

---

### Post by xeth_delta on 2007-11-29
> **Ice_cone said:**
> If I enabled xgl I get this results:
user@x31-laptop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

Even scrolling a webpage is now very slow

I got a yes if I remove xgl.
anyone can help me?
thanks

What do you mean by enabling xgl? What driver are you using? What version of Ubuntu are you using?

---

### Post by Ice_cone on 2007-11-29
> **xeth_delta said:**
> What do you mean by enabling xgl? What driver are you using? What version of Ubuntu are you using?

sorry for not giving the details
enabling xgl means installing it, and it is actually running.
I've used the ati driver, ubuntu 7.10.

(now i'm trying the radeon driver, but xgl is not enabled even though i've installed it)
thanks

---

### Post by xeth_delta on 2007-11-29
How did you install xgl? Did you use the package management system?
I used to own a laptop with an integrated ati graphics card corresponding to a similar period as yours. If I recall correctly, there was no complete 3d support in xgl for my card, and that is probably the case with yours.

Why are you trying to use xgl? Do you want to use beryl/compiz-fusion? If that is the case you can use the regular X.org server and AIGLX. That's what I did on my old laptop and also on my new one.

---

### Post by Ice_cone on 2007-11-29
> **xeth_delta said:**
> How did you install xgl? Did you use the package management system?
I used to own a laptop with an integrated ati graphics card corresponding to a similar period as yours. If I recall correctly, there was no complete 3d support in xgl for my card, and that is probably the case with yours.

Why are you trying to use xgl? Do you want to use beryl/compiz-fusion? If that is the case you can use the regular X.org server and AIGLX. That's what I did on my old laptop and also on my new one.

thanks
i installed by command (sudo apt-get install xserver-xgl)
i want to run compiz fusion, i used to be able to run it with 'ati' driver with xgl, but hardware acceleration is disabled, so it is very slow.
then i installed the ati proprietary driver (version 8.433 i think) which i downloaded online, but then after I login (typed password) it failed and restarted X
I used "sudo aticonfig --initial -f" to reset everything.  It prompt me when I login again and I chose the 'radeon' driver.
Now i've xgl installed but it is not started.
what can I do?
thanks very much

---

### Post by xeth_delta on 2007-11-29
I suppose you have access to the command line on that machine, so I would start by restoring xorg as the default X11 server.

Make sure xserver-xorg is installed:
```
sudo aptitude search xserver-xorg
```
It should show something like
```
i A xserver-xorg
```

Very important, make a back-up of your /etc/X11/xorg.conf

Now, remove xserver-xgl
```
apt-get remove xserver-xgl
```

try starting X11
```
startx
```
Please, make sure you start X11 as a normal user.
In case of error it will show some output, please post it here.

---

### Post by Ice_cone on 2007-11-29
> **xeth_delta said:**
> I suppose you have access to the command line on that machine, so I would start by restoring xorg as the default X11 server.

Make sure xserver-xorg is installed:
```
sudo aptitude search xserver-xorg
```
It should show something like
```
i A xserver-xorg
```

Very important, make a back-up of your /etc/X11/xorg.conf

Now, remove xserver-xgl
```
apt-get remove xserver-xgl
```

try starting X11
```
startx
```
Please, make sure you start X11 as a normal user.
In case of error it will show some output, please post it here.

thanks
but i'm now fine with GUI
i just can't start compiz fusion again

---

### Post by xeth_delta on 2007-11-29
Can you check if you have 3D acceleration using the radeon driver?
```
glxinfo | grep -i direct
```

If the answer is yes, then you can try using some guides from this forum on how to install compiz fusion.

On my current laptop I have Feisty and Beryl, so you might not have to follow the same steps i did.

Good luck!

---

### Post by Ice_cone on 2007-12-01
~$ glxinfo | grep -i direct
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual

---

### Post by xeth_delta on 2007-12-01
> **Ice_cone said:**
> ~$ glxinfo | grep -i direct
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual

Hmmm, that is not the output I was expecting, I was hoping for something like:
```
glxinfo | grep -i direct
direct rendering: Yes
```

Please run just **glxinfo** and post the output between code tags. ATIFGLRXDRI must have something to do with the ati proprietary driver, which I am not sure supports 3D hardware acceleration for your card. Are you sure you are using the X.org open source driver?

Please, first make a back-up of your xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bkp
```
Then::
```
sudo nano /etc/X11/xorg.conf
```
look for **Section "Device"** and make sure you have **radeon** for the driver, not fglrx.

Make sure you saved the file (control o), and after that, either kill the X11 server (control-Alt-Backspace) or reboot.

---

### Post by Ice_cone on 2007-12-01
my xorg.conf session:
Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

The driver is radeon

glxinfo:
~$ glxinfo
name of display: :0.0
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x24 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x25 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x26 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x27 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x28 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x29 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2a 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2b 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2c 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2d 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2e 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x2f 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x30 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x31 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x32 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
0x55 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

thanks

---

### Post by xeth_delta on 2007-12-01
Please do the following:
```
aptitude search fglrx
```
and post the output.

---

### Post by Ice_cone on 2007-12-01
> **xeth_delta said:**
> Please do the following:
```
aptitude search fglrx
```
and post the output.
```

p   fglrx-control                   - Control panel for the ATI graphics acceler
v   fglrx-driver                    -                                           
v   fglrx-driver-dev                -                                           
p   fglrx-kernel-source             - ATI binary kernel module source           
p   xorg-driver-fglrx               - Video driver for ATI graphics accelerators
p   xorg-driver-fglrx-dev           - Video driver for ATI graphics accelerators

```
note: i've just reconfigured the x server using dpkg-reconfigure xserver-xorg
i chose the ati driver.  however, the output of glxinfo is still unchanged
edit: just like before, i can't install xserver-xgl or X will crash after login
thanks

---

### Post by xeth_delta on 2007-12-01
> **Ice_cone said:**
> ```

p   fglrx-control                   - Control panel for the ATI graphics acceler
v   fglrx-driver                    -                                           
v   fglrx-driver-dev                -                                           
p   fglrx-kernel-source             - ATI binary kernel module source           
p   xorg-driver-fglrx               - Video driver for ATI graphics accelerators
p   xorg-driver-fglrx-dev           - Video driver for ATI graphics accelerators

```
note: i've just reconfigured the x server using dpkg-reconfigure xserver-xorg
i chose the ati driver.  however, the output of glxinfo is still unchanged
edit: just like before, i can't install xserver-xgl or X will crash after login
thanks

I still believe you don't need to install xserver-xgl to run compiz. When run dpkg-reconfigure xserver-xorg, can you choose the radeon driver?

Please also attach your /etc/X11/xorg.conf to your next post.

---

### Post by Ice_cone on 2007-12-01
> **xeth_delta said:**
> I still believe you don't need to install xserver-xgl to run compiz. When run dpkg-reconfigure xserver-xorg, can you choose the radeon driver?

Please also attach your /etc/X11/xorg.conf to your next post.
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
        Option 		"Buttons" 		"7"
        Option 		"ButtonMapping" 	"1 2 3 6 7"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
        Option          "AGPMode" "4"
        Option          "AGPSize" "64" # default: 8
        Option          "RingSize" "8"
        Option          "BufferSize" "2"
        Option          "EnablePageFlip" "True"
        Option          "EnableDepthMoves" "True"
        Option          "RenderAccel" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```
I can choose radeon but I didn't.
thanks

---

### Post by Ice_cone on 2007-12-01
YOOOOO!!!
you're right!
I can now enabled compiz fusion!
thank you very much!

---

### Post by xeth_delta on 2007-12-01
> **Ice_cone said:**
> YOOOOO!!!
you're right!
I can now enabled compiz fusion!
thank you very much!

Glad to hear that! So, how did you solve the problem, choosing to radeon while reconfiguring?

Xeth

---

### Post by Ice_cone on 2007-12-01
> **xeth_delta said:**
> Glad to hear that! So, how did you solve the problem, choosing to radeon while reconfiguring?

Xeth

I'm not too sure.
I did too many things
perhaps it's these lines:        
 Option          "AGPMode" "4"
        Option          "AGPSize" "64" # default: 8
        Option          "RingSize" "8"
        Option          "BufferSize" "2"
        Option          "EnablePageFlip" "True"
        Option          "EnableDepthMoves" "True"
        Option          "RenderAccel" "true"

thanks

---

### Post by ubuntu.daemon on 2007-12-25
wow, omg thank you jesus.  whatever was in ur xorg.conf like fixed mine 10 fold.  I am using an x31 as well, but ya your xorg def improved me!

cheers!
:popcorn:

---

### Post by Buzz Lightyear on 2008-04-04
Heya ice_cone could you please post your full xorg.conf for those who want to feel as happy as you do ?

Thx Buzz!

---

### Post by ubuntu.daemon on 2008-04-04
im assuming you have an x31 as well?

---

