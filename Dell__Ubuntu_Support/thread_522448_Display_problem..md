---
title: "Display problem."
date: 2007-08-10
forum: Dell  Ubuntu Support
---

### Post by kellyjosephprice on 2007-08-10
Hi, I'm new to Ubuntu, and have been loving everything about it.  Except for this one problem.

I bought this Dell laptop a few months ago, and almost immediately happened to spill a beer directly on the keyboard.  The display became distorted with horizontal and vertical lines.  I shut it down and left it off for the night hoping that it would go away on its own.  And it did.
More or less randomly, I would boot it up and the display would be distorted similarly, and this tended to go away with a reboot.  However, one time, it stopped displaying at the normal resolution and reverted to 640x480, which is especially annoying since it's a widescreen laptop.
I wasn't able to find someone with a similar problem on these forums, and I ended reinstalling Kubuntu, which, to my suprise fixed the problem. 
Today, I was watching a movie in fullscreen, so I guess I didn't notice the powermanager warning and the battery ran out, and now it's back to the distortion and poor resolution.  Help, please.

---

### Post by ridgeland on 2007-08-10
Do you know how to change resolution from the menu and set options in /etc/X11/xorg.conf?  This could restrict the options it considers valid.
Sounds like there may be a beer issue though.  The heat of the PC should evaporate the liquid away but if there is a mechanical problem maybe a shop could clean it up.

---

### Post by kellyjosephprice on 2007-08-10
I tried changing the resolution from the system settings, but it doesn't offer the widescreen resolutions, and if I do change the resolution, the distortion is worse. 
No, I am not familiar with editing xorg.conf.

---

### Post by ridgeland on 2007-08-10
xorg.conf holds the options for screen resolution.

Always make a backup before editing a system file:
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.20070810

$ sudo gedit /etc/X11/xorg.conf
Here is what my "Screen" section has:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation GeForce 7300 LE"
    Monitor        "FPD1810"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```
See the default depth - that says start with 24 bit color (I think) then under the subsection for Depth 24 is the options it offers.  The default is the first one.  I changed the order to have 1280x1024 be the first one.
xorg.conf also says what driver you're using.  I use Nvidia not nv for this desktop.  This cannot help a hardware problem but it may help if it's just a settings issue.

---

### Post by kellyjosephprice on 2007-08-10
Thank you for the direction, I have to go for the moment.

---

### Post by kellyjosephprice on 2007-08-10
Part of my xorg.conf file:

```
Section "Screen"
   Identifier "Default Screen"
   Device "ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
   Monitor "Generic Monitor"
   DefaultDepth 24
   SubSection "Display"
      depth 24
      virtual 640 480
      modes"640x480@60"
   EndSubSection
EndSection
```

---

### Post by kellyjosephprice on 2007-08-10
So I deleted the line virtual desktop 640 480, and changed the resolution and all is well.  Thanks again.  
Do you have any idea what caused that?

---

### Post by ridgeland on 2007-08-10
Glad it helped.  Hope it stays OK.
Don't know what the virtual line is about.  Don't know what is causing changes.  Only root can edit that system file.  So if it's getting abused it has to be by something with system admin rights, like another system program.
I'm surprised that you want 640x480 and not something bigger.
Usually there is a section to control the vertical and horizontal refresh rates like:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSectio
```
You need the specs of your Display to set the ranges.

---

