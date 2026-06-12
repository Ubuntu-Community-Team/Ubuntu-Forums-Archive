---
title: "Ubuntu 7.10 and ati and compiz"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by jtouso on 2007-10-19
Hi,
Wondwerful Ubuntu 7.10!!

I have ATI/Radeon 9550 agp 250 Mb graphic chart and I' m using Ubuntu 7.10 in live/mode before installation to know the new effects and programs. It looks and feel very good and fast (remember live-mode) but I can' t use the compiz effects...System...Preferences...Appearance...Visual Effects...Extra says NO and I can' t use the new compiz-fussion effects.
The live-mode uses ati driver (xorg free driver) and my Direct rendering says YES
Is it possible to use these effects in live-mode or may I need to install to use it?
Thanks
Jose

---

### Post by farscape on 2007-10-20
I have the same Video card and the same problem. BUT I am not in live mode. It's a fresh install of 7.10. I am using the restricted driver (fglrx). Any ideas? I hate to have to put my Nvidia 4200 back in.

---

### Post by jelofson on 2007-10-20
I have an ATI 9700 mobility and was using the fglrx driver. As far as I know, you can't use the desktop effects with the restricted driver. However, if you disable the restricted driver and restart, you might be able to get the desktop effects to work by editing your xorg.conf file.

You could try this:

launch the terminal

cd /etc/X11
sudo vi xorg.conf

Look for a section near the bottom that says 
Section "Extensions"
        Option "Composite" "Disable"
EndSection

Change the Disable to Enable and restart your xsession (Ctrl + Alt + Backspace)
Then go back to the Preferences/Appearances and enable some desktop effects.

Maybe this will work for you.

---

### Post by amarkovits on 2007-10-26
Actualy it is realy simple

see this: [http://amarkovits.blogspot.com/2007/10/ubuntu-710-compiz-ati.html](http://amarkovits.blogspot.com/2007/10/ubuntu-710-compiz-ati.html)

just put the Composite on "1" instead of "0"  (in the extension section of your xorg.conf file)
install xserver-xgl (sudo apt-get install xserver-xgl)
restart your X-server (restart or CTRL+ALT+BACKSPACE)
and now you can enable your Desktop effects!

It worked great for me on a IBM T60 with ATI X1300.

---

### Post by michael37 on 2007-10-26
Can't use it in live mode, only when installing. 

[thread=569654]Especially useful if you are upgrading from Feisty[/thread]

---

### Post by VCSkier on 2007-10-26
Running compiz on a system with the fglrx driver prior to release 8.42.3 requires the usage of XGL, which is not easy to setup up, and has many limitations.  This current release of fglrx (8.42.3), which was just announced 3 days ago, now supports AIGLX, making compiz much easier to run, and making XGL no longer necessary.  Give things a week or so for the dust to settle around this new driver, as people iron out the problems in the installation method, and then you should be able to install it and have great compositing support quite easily.  Good luck.

---

### Post by bribaetz on 2007-10-26
okay so i install all the stuff for the advanced settings but i messed up my card driver when i messed with it to see if any of them would work because i hadn't read all the threads so my comp is fine at this piont its a little crapy with the video. my card environment thingy will have a blank at the top of the window bar where you move it or close it. so i just disable it and i messed with my driver some more and i also mess with my screen settings size etc. now every time i try to log in it takes me back to the log in screen unless i use the failsafe_gnome thing with out using any extra scripts which would be okay if my mouses left click and right click weren't backwards. by the way my video card is "ATI rage 128" well thats my problem.

---

### Post by michael37 on 2007-10-26
> **VCSkier said:**
> Running compiz on a system with the fglrx driver prior to release 8.42.3 requires the usage of XGL, which is not easy to setup up, and has many limitations.  This current release of fglrx (8.42.3), which was just announced 3 days ago, now supports AIGLX, making compiz much easier to run, and making XGL no longer necessary.  Give things a week or so for the dust to settle around this new driver, as people iron out the problems in the installation method, and then you should be able to install it and have great compositing support quite easily.  Good luck.

Xgl on Gutsy Gibbon 7.10 is incredibly easy to set up.     Ignore this FUD while you are ahead.

For Xgl on ATI, see the thread I mentioned above (with Feisty upgrade instructions too).

AIGLX in 8.42 is very slow, in fact much slower than Xgl.  Many threads dedicated to the subj.

---

### Post by dewey on 2007-10-26
```
sudo apt-get install xserver-xgl
```
Restart X or reboot, whichever is easiest for you, and voila, you're done.

---

### Post by michael37 on 2007-10-26
> **dewey said:**
> ```
sudo apt-get install xserver-xgl
```
Restart X or reboot, whichever is easiest for you, and voila, you're done.

You got to enable the restricted driver before installing Xgl.

---

### Post by Bazirker on 2007-10-27
XGL is super easy to set up in Gutsy.

I am using XGL with ATI's proprietary drivers, first 8.41 then I upgraded to 8.42.  However, my performance with both drivers isn't as good as when I was running compiz in Feisty (also using ATI's drivers, whatever they currently were at the time.)  Whenever I load up app's (like firefox) that take up the whole screen, effects get a lot slower.  Any idea why?  It's driving me nuts having really chunky cube rotations.

---

### Post by michael37 on 2007-10-27
> **Bazirker said:**
> XGL is super easy to set up in Gutsy.

I am using XGL with ATI's proprietary drivers, first 8.41 then I upgraded to 8.42.  However, my performance with both drivers isn't as good as when I was running compiz in Feisty (also using ATI's drivers, whatever they currently were at the time.)  Whenever I load up app's (like firefox) that take up the whole screen, effects get a lot slower.  Any idea why?  It's driving me nuts having really chunky cube rotations.

Post output of fglrxinfo -display :0
and 
fglrxinfo -display :1
please

---

### Post by Bazirker on 2007-10-27
```
$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6958 Release

$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
```

I'm on a laptop...what does the difference between the two displays mean?  I don't like that Mesa business!  :(

---

### Post by michael37 on 2007-10-27
> **Bazirker said:**
> ```
$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6958 Release

$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)
```

I'm on a laptop...what does the difference between the two displays mean?  I don't like that Mesa business!  :(

Xgl uses so-called screen:0.  They are virtual elements and have no relations to actual monitors.  I have a laptop too and I don't have this problem (it actually has no relations to laptops).  

Your performance is horrendously slow because you are actually NOT using the ATI enhanced driver for your Xgl!!! 

Edit your xorg.conf file using ```
gksudo gedit /etc/X11/xorg.conf
```
and see if you have Extensions section.  If yes, edit it like this.  If no, just copy paste the lines below at the end of the file.

```

Section "Extensions"
Option "AIGLX" "off"
Option "Composite" "off"
EndSection

```

Save, exit, reboot and you should see quite a bit performance improvements.

---

### Post by Bazirker on 2007-10-27
Nope, I've got that in my xorg.conf.  Here's my xorg.conf file (although I removed the sections concerning my input devices since they're not relevant.)

```
Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection


Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
EndSection

Section "Extensions"
Option "AIGLX" "off"
Option "Composite" "off"
EndSection
```

---

### Post by Bazirker on 2007-11-04
Solved!  I ran this code then rebooted:

```
sudo apt-get --purge remove xorg-driver-fglrx
sudo apt-get install xorg-driver-fglrx
```

Now my fglrxinfo shows this:

```
~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)

~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```

Now my compiz setup is speedy!  Anyone know what that "XFree86-DRI missing" business means?  Is there any reason why I should care given that compiz is now running fast?

---

### Post by michael37 on 2007-11-04
> **Bazirker said:**
> Solved!  I ran this code then rebooted:

```
sudo apt-get --purge remove xorg-driver-fglrx
sudo apt-get install xorg-driver-fglrx
```

Now my fglrxinfo shows this:

```
~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 2.0.6473 (8.37.6)

~$ fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```

Now my compiz setup is speedy!  Anyone know what that "XFree86-DRI missing" business means?  Is there any reason why I should care given that compiz is now running fast?

Nice way to find and fix the problem. I'll certainly keep it in mind.

The XFree86-DRI (XFree86 version of Direct Rendering Infrastructure) is indeed missing on display :1 which is where Xgl runs.  Instead, our driver provides an alternative implementation called FGLRXDRI.  If you want to check if you have it running, check grep FGLRXDRI /var/log/Xorg.*.log

This is subject to change in the near future -- probably by early/mid 2008 ATI will release drivers with "more standard" implementations.  There are versions that are kinda half-way there now (8.42.3 driver), but I'd stay away from it for now.

---

### Post by chchyong89 on 2007-11-05
i am going to break down my head.. i am noob and new to ubuntu linux
i just download the ubuntu 7.10..
the following spec is my PC spec
P4 530 3.0Ghz
MSI P35 NEO
2X1GB DDR2-667 corsair, 2X1GB DDR2-667 kingston
Gecube ATi X300 128MB DDR
80GB SATA

i found it ubuntu can make aweful affect from youtube..
whole week, i have google for it how to modify it..

first. i know it need beryl.. then now i know that on 7.10 got COMPIZ installed already
then need to go restrict driver and enable it... then get update the OS...
i am going mad.. almost all section teach me different ways to enable effect..
i try go to ATI.com download the driver and sudo it... i am very happy the driver installed.. but i don't think it work.. and it only have 800X600 and 640X480 to apply.. i have try whole week.. format, install , fail, format, install, fail again.......i am going mad, please somebody show me the proper ways please...

maybe i am really a noob, i have no idea totally how to enable it..
problem i found that make me to format it..
-it lag a lot after i follow the steps.. i forgot which one already .. too many..
-after follow some steps and reboot, the mouse become X shape and ask me to continue.. erm i forgot wat it said already, it's about VGA driver...
-then when i continue, every windows when i move it.. lag a lot
-and i go to the appearance there turn on effect, cannot at all!
-steps make me fail again... i have done what they teach me from the webs, why??!!!


i found on this topic..
and i come with fresh install linux
it just weird
just put the Composite on "1" instead of "0" (in the extension section of your xorg.conf file)
install xserver-xgl (sudo apt-get install xserver-xgl)
restart your X-server (restart or CTRL+ALT+BACKSPACE)
and now you can enable your Desktop effects!
.. i done it without problem.. 
fail also.. it lag alot when i come back to ubuntu..! weird..

i have done many steps.. but all fail!! please somebody teach me the proper ways..
now i have a clean install ubuntu waiting for any pro guide me out from step and step..

sorry for my broken english, maybe i am really a stupid..:confused:

---

