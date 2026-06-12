---
title: "Resolution not supported"
date: 2009-05-04
forum: General Help
---

### Post by Deviance1 on 2009-05-04
Hello. I have the following problem. I am using 15 inch monitor, and it was working quite well with a 1024x768 resolution under Windows. Right now, I have attached this monitor to my Ubuntu box, and the maximum resolution I can get is 800x600. Under Windows I noticed that 1024x768 was only available when setting refresh rate to 43 hertz, however I have tried this on Ubuntu and it just didn't work. What could I be doing wrong?

Thanks,
Ray

---

### Post by freonchill on 2009-05-04
what is your video card and monitor?

---

### Post by Deviance1 on 2009-05-04
> **freonchill said:**
> what is your video card and monitor?

Video card is ATI Radeon. Monitor is a quite old Samtron for which I can't find any manual.

---

### Post by BslBryan on 2009-05-04
Also, it's sad to say that this is a fairly common problem in Ubuntu.  However, just to let you know, 1024x768 is supported in Ubuntu.  

:lol:  I just pictured every Ubuntu user having an 800x600 mini pc.

EDIT: What version of Ubuntu are you using?

---

### Post by Deviance1 on 2009-05-04
> **BslBryan said:**
> Also, it's sad to say that this is a fairly common problem in Ubuntu.  However, just to let you know, 1024x768 is supported in Ubuntu.  

:lol:  I just pictured every Ubuntu user having an 800x600 mini pc.

EDIT: What version of Ubuntu are you using?

I know that 1024x768 IS supported. I am not a first time user. I have been with Linux for over 5 years, and using it as server platform. It's the first time I try it as a desktop user :)

The version is 8.04

---

### Post by freonchill on 2009-05-04
though i dont have experience with it, i know that ati cards have drivers (either restricted or from ati directly)

as i have had problems in the past with nvidia restricted driver (and that you dont seem to have that) you might want to try those...

i was limited to 800x600 till i installed the restricted drivers for my laptop with nvidia gpu, then i was able to get to the 1920x1200 resolution of my LCD

---

### Post by BslBryan on 2009-05-04
My mistake.  :P

Anyway, try this:

```
sudo apt-get install envyng-qt
```
This will install a program called Envy.  This program installs and configures the drivers for nVIDIA and ATI graphics cards.  

Since you're no stranger to the terminal, if you want to install the text-only version (as in, no GUI) you can download this instead:
```
sudo apt-get install envyng-core
```

Then, you select it from Applications --> System Tools

or, if you like using the terminal, run this in a shell:
```
sudo envyng -t
```

Then, follow the instructions for ATI.  I'd suggest the Automatic Hardware Detection option, by the by.

If you have any doubts after installation but before use, run this:
```
man envyng
```

Hope this helps. 

Post your decisions/results here, please?

Good luck. :)

---

### Post by michy99 on 2009-05-04
There may be some useful information in some of these:

[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Deviance1 on 2009-05-04
> **BslBryan said:**
> My mistake.  :P

Anyway, try this:

```
sudo apt-get install envyng-qt
```This will install a program called Envy.  This program installs and configures the drivers for nVIDIA and ATI graphics cards.  

Since you're no stranger to the terminal, if you want to install the text-only version (as in, no GUI) you can download this instead:
```
sudo apt-get install envyng-core
```Then, you select it from Applications --> System Tools

or, if you like using the terminal, run this in a shell:
```
sudo envyng -t
```Then, follow the instructions for ATI.  I'd suggest the Automatic Hardware Detection option, by the by.

If you have any doubts after installation but before use, run this:
```
man envyng
```Hope this helps. 

Post your decisions/results here, please?

Good luck. :)

This doesn't work either. It installed the driver, asked me to restart and after restart displayed a configuration box, telling me that the computer is running with low display settings and whether I wanted to fix that. It allowed me to select monitor type and resolution (Yes, it displayed 1024x768 as available, but specified 60 hertz as the lowest possible), but when I did select 1024x768 and 60 Hertz, it defaulted back to 800x600. As I said before, the same monitor was running the right resolution on Windows at 43 hertz, so this is definitely refresh rate problem, but I can't seem to figure it out, since I'm more into console than into GUI :)

---

### Post by BslBryan on 2009-05-04
Hmm...  What about activating the proprietary drivers?  That seems easy enough.  

You can also try editing your xorg.conf file, and adding in your screen resolution. 

Actually, can you post the results of 
```
cat /etc/X11/xorg.conf | grep Driver
```

---

### Post by michy99 on 2009-05-04
Have you tried adding your Horizontal Sync and Vertical Refresh to the Monitor section of xorg.conf? That has worked for me on occasion.

---

### Post by Deviance1 on 2009-05-04
> **BslBryan said:**
> Hmm...  What about activating the proprietary drivers?  That seems easy enough.  

You can also try editing your xorg.conf file, and adding in your screen resolution. 

Actually, can you post the results of 
```
cat /etc/X11/xorg.conf | grep Driver
```

Xorg is using the "ati" driver, and the lines in xorg.conf lists only one resolution which I added by hand and it is 1024x768. Currently Ubuntu does not list any restricted driver in the restricted drivers manager.

---

### Post by BslBryan on 2009-05-04
I think I have a suggestion, but first, can you give me the output of 
```
lspci -nn | grep VGA
```

---

### Post by Deviance1 on 2009-05-04
> **BslBryan said:**
> I think I have a suggestion, but first, can you give me the output of 
```
lspci -nn | grep VGA
```

There you go:

deviance@dc-110:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 If [Radeon 9000] [1002:4966] (rev 01)
deviance@dc-110:~$

---

### Post by BslBryan on 2009-05-04
One final thing before instructions, I promise.  Sorry. :)
```
glxinfo | grep vendor

```

---

### Post by Deviance1 on 2009-05-04
> **BslBryan said:**
> One final thing before instructions, I promise.  Sorry. :)
```
glxinfo | grep vendor

```
 
Sure, no problem :)

deviance@dc-110:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
deviance@dc-110:~$

---

### Post by BslBryan on 2009-05-04
Okay, try this:
```
sudo apt-get remove --purge libgl1-mesa-swx11 libgl1-mesa-swrast libgl1-mesa-glx+ libglu1-mesa+
```

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Choose ATI as your driver.  If that doesn't work, then we need to run this:
```
sudo apt-get install --reinstall xorg-driver-fglrx fglrx-control linux-restricted-modules && sudo depmod -a
```
then:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
And choose fglrx as your driver.

Also, remember to reload your x server when you attempt to change drivers.

Good luck.  A couple more ideas if this doesn't work, but we'll have to undo some stuff, unfortunately.  So...  Here's to hoping this works out! :P

---

### Post by Deviance1 on 2009-05-04
I have tried dpkg-reconfigure -phigh xserver-xorg before and it does not allow me to select a driver. All it says is that a "Possibly customized xorg.conf has been overwritten" or something like that. Same this time.

---

### Post by BslBryan on 2009-05-04
Then
```
gksudo gedit /etc/X11/xorg.conf
```
and manually change them there.

---

### Post by Deviance1 on 2009-05-04
That's what I did just before you posted this :)
Well, X attempts to start, but we're back to the "Ubuntu is running in low-graphics mode" message. Changing anything there does not have any effect - it just defaults back to 800x600 as I said before.

---

### Post by BslBryan on 2009-05-04
```
glxinfo | grep vendor
```

Still outputs SGI, right?

---

### Post by Deviance1 on 2009-05-04
True

---

### Post by michy99 on 2009-05-04
Here's what I have in the Monitor section of xorg.conf. Of course, your values would be different.

```
Section "Monitor"
	Identifier	"Configured Monitor"
	HorizSync       30-85
       VertRefresh     50-160

EndSection
```

---

### Post by Deviance1 on 2009-05-04
I have the same sections. As I said before, I am sure that experimenting with the hertz values would solve the problem, but... I have yet to find the right ones.

Since the monitor is old, I can't seem to find a manual for it and that makes all this thing very difficult to solve.

---

### Post by BslBryan on 2009-05-04
Okay, good.  Now, 
```
sudo apt-get install xserver-xorg-video-ati
```

Then modify your xorg.conf like this:
```
Section "Device"
Identifier "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Driver "ati"
BusID "PCI:1:0:0"
#Uncomment if GARTSize is 64.
#Option "GARTSize" "64"
Option "MergedFB" "off"
Option "XAANoOffscreenPixmaps" "true"

EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Virtual 1024 768
Modes "1024x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"

# Uncomment if you have a wacom tablet
# InputDevice "stylus" "SendCoreEvents"
# InputDevice "cursor" "SendCoreEvents"
# InputDevice "eraser" "SendCoreEvents"
InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection 
```

I really hope this works.

Good luck, again. :)

---

### Post by Deviance1 on 2009-05-04
Nah.. Same old "Ubuntu is running in low graphics mode" message. I guess I'll just get a new monitor :D

---

### Post by BslBryan on 2009-05-04
:-k  I'm stumped here.  

I'm really sorry I couldn't be of greater help here.  

If I think of anything else, I'll post, but for now I've got a bit of work of my own to do.

Best to you, Deviance1, and good luck. :)

---

### Post by Deviance1 on 2009-05-04
Thanks. Anyway, you've been of great help :)

---

### Post by ookmarc on 2009-05-07
> **Deviance1 said:**
> I have the same sections. As I said before, I am sure that experimenting with the hertz values would solve the problem, but... I have yet to find the right ones.

Since the monitor is old, I can't seem to find a manual for it and that makes all this thing very difficult to solve.

The problem is probably the VertRefresh line: The xorg.conf file apparently has '50-160', that doesn't include the working 1024x768@43 Hz  you had for Windows. If you allow a refresh of '40-...' the X server may detect you monitor mode correctly...

If  no default 1024x768 mode found within the range, use the 'gtf' tool  to create a modeline:
gtf 1024 768 43 gives for instance:

  # 1024x768 @ 43.00 Hz (GTF) hsync: 33.88 kHz; pclk: 43.91 MHz
  Modeline "1024x768_43.00"  43.91  1024 1056 1160 1296  768 769 772 788  -HSync +Vsync

This line can be added to the "Monitor" section of xorg.conf and requested as
Mode "1024x768_43.00" in the "Screen->Display" section.

Come to think of it:
Perhaps Windows is reporting a 85Hz interlaced mode as 43Hz...
In that case this modeline could do the trick:

Modeline "1024x768@85i"     42.91  1024 1056 1216 1248    768  784  790  807 interlace

---

