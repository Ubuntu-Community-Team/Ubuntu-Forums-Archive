---
title: "Cannot set the max resolution in a D600"
date: 2008-03-17
forum: Dell  Ubuntu Support
---

### Post by supremedalek on 2008-03-17
When I installed ubuntu 7.10 in my latitude D600, it correctly installed the open source ATI drivers,

```
raub@monaco:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.
raub@monaco:~$ 
```

as my video card

```
raub@monaco:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 01)
raub@monaco:~$ 
```

Is a Radeon 9000 thingie. I also checked that  xorg-driver-fglrx,  is not reported installed while libgl1-mesa-glx and libgl1-mesa-dri are. Anywhoo, right now it only does 1024x768.  When I had this laptop running XP, I could get much better resolution.  So, based on what I read in [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), my card is supported by the open source driver. So I decided to, based on what was described in that page, see if I can increase my max resolution. I went to my /etc/X11/xorg.conf, right to the Screen section,

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]
"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768"
        EndSubSection
EndSection
```

and, under the Screen section, changed

```
                Modes           "1024x768"
```

to

```
                Modes           "1440x900" "1024x768"
```

and then restarted gdm. Well, it did not seem to work.  In fact, when I checked /var/log/Xorg.0.log, it seems to have a few problems:

```
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon Mobility 9000 (M9) Lf (AGP)" (ChipID = 0x4c66)
(--) RADEON(0): Linear framebuffer at 0xe8000000
(II) RADEON(0): AGP card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
[...]
(II) RADEON(0): Added native panel mode: 1024x768
(WW) RADEON(0): Mode 1440x900 is out of range.
(WW) RADEON(0): Valid FP modes must be between 320x200-1024x768
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)

```

What am I missing here? :confused:

---

### Post by klaxian on 2008-04-08
Have you found a solution to this problem?  I am having the same issue with a fresh install of hardy.  Thanks!

---

### Post by supremedalek on 2008-04-09
Nope.  I am still stuck.  I think I will try to replace the free driver with the ATI one and see if that solves the problem.

---

### Post by The Cog on 2008-04-09
My D600 has always defaulted to 1400x1050 which I believe is the native LCD resolution. Attached is my xorg.conf.

You might also find the command **xrandr** interesting.

---

### Post by supremedalek on 2008-04-15
I tried to edit my xorg.conf file and even rebooted the machine. Same output. Here is the output for xrandr:

```
raub@monaco:~$ xrandr 
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1024 x 1024
VGA-0 disconnected (normal left inverted right)
DVI-0 disconnected (normal left inverted right)
LVDS connected 1024x768+0+0 (normal left inverted right) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3     59.9  
   640x480        59.9  
S-video disconnected (normal left inverted right)
raub@monaco:~$ 

```

The log file still thinks 1024x768 is the native mode. :(

---

### Post by mahughesnh on 2008-04-15
Sorry for butting in but I think I know what the problem is.

Not all D600 screens display 1400 x 1050.  There were two screens available if I remember correctly.  One with 1024 x 768 as the maximum, the more expensive screen was capable of 1400 x 1050.  

I have a D600 as well and when I replaced the screen due to a accidental drop I had to make sure of getting the right one as I was replacing a 1400 x 1050.

Correct me if I am mistaken, but I believe this to be true

Mike

---

### Post by supremedalek on 2008-04-15
Now I am really confused: if that is the case, why I could do higher resolutions than 1024x768 under XP? :confused:

My brain hurts!

---

### Post by mahughesnh on 2008-04-16
I can see why you would feel that way.  I did not know that you could access higher resolutions under XP.  I do know that Ubuntu, and any other distro that I may install, recognizes my screen at 1400 x 1050 by default.

Here is my xrandr output:

Screen 0: minimum 320 x 200, current 1400 x 1050, maximum 1400 x 1200
VGA-0 disconnected (normal left inverted right)
DVI-0 disconnected (normal left inverted right)
LVDS connected 1400x1050+0+0 (normal left inverted right) 0mm x 0mm
   1400x1050      60.0*+
   1280x800       60.0  
   1280x768       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right)

And this is the video section of my xorg.conf:

Section "Device"
	Identifier	"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection


I would be very interested to hear if any of this helps anyone else.

Mike

---

### Post by supremedalek on 2008-04-26
mahughesnh, your xorg.conf entries are very similar to what The Cog posted. I just think that laptop does not like ubuntu. Incidentally I tried the commercial ati drivers and it was much worse; I had to go to command line mode and then comment/uncomment the appropriate entries to go back to the free driver.

Also, if this is relevant, when I boot the machine I do not get the normal ubuntu boot screen (i.e. first the splash screen then the text pages showing what is going on in the boot process). Instead I get a black screen until the login screen.

I am this close of wiping the HD and then trying centos or reinstalling ubuntu to see if there is a difference. Would it be? I honestly do not know why it should, but hey. Actually, I still have a knoppix live cd around...

---

