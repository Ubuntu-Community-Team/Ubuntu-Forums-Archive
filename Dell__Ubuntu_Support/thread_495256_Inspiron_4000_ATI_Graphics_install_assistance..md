---
title: "Inspiron 4000 ATI Graphics install assistance."
date: 2007-07-07
forum: Dell  Ubuntu Support
---

### Post by nc_jed on 2007-07-07
Team,
Recently, I inherited a Dell Inspiron 4000 (700Mhz, 256 MB RAM, 9GB HD, Ralink 802.11g based PCMCIA card).  I installed Xubuntu 7.04 with relative ease (considering the age of the machine).  The only glitch thus far has been the 800x600 default resolution I seem to be stuck with.   I've been trying to get the stock ATI 3D driver installed on this machine, but think it may be too old (see results of lspci):

```
01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)
```

Everything I see is Radeon this and Radeon that.  I have followed this [link]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") until my eyes have crossed, but to no avail.  I see there are a few others having miscellaneous issues and have tried to follow along with the suggestions being given to them, but we seem to not be having the same symptoms.

Is this in fact a 'too old' card that is not supported by the drivers mentioned in the thread above, or am I just not trying hard enough?

Regards, Blake

---

### Post by angryfirelord on 2007-07-13
The fglrx driver doesn't work for old cards. You have to go into your xorg.conf and change the driver to say "ati".

---

### Post by thetictacaddict on 2007-08-04
I was having the same problem on my Inspiron 4000, and I have just found the solution!  I found a "driver" RPM on Dell's website for RedHat 7, which turned out to contain an XFree86 config file.

Change your driver from "ati" to "r128",  and under your monitor section, add
```
HorizSync     31.5 - 48.5
VertRefresh   60
Modeline "1024x768"   65.000  1024 1048 1065 1344   768  770  776  806
```

At least that worked for me.  You may still need to change your resolution settings under XFCE (I had to in Gnome).

Here's the full config file from the RPM, in case it helps.
```
Section "ServerLayout"
	Identifier     "XFree86 Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "pex5"
	Load  "record"
	Load  "xie"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "keyboard"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option      "Protocol" "PS/2"
	Option      "Device" "/dev/mouse"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync     31.5 - 48.5
	VertRefresh   60
	Modeline "1024x768"   65.000  1024 1048 1065 1344   768  770  776  806
EndSection

Section "Device"
	### Available Driver options are:-
        #Option     "NoAccel"
        #Option     "SWcursor"
        #Option     "HWcursor"
        #Option     "Dac6Bit"
        #Option     "Dac8Bit"
        #Option     "ForcePCIMode"
        #Option     "CCEPIOMode"
        #Option     "CCENoSecurity"
        #Option     "CCEusecTimeout"
        #Option     "AGPMode"
        #Option     "AGPSize"
        #Option     "RingSize"
        #Option     "VBListSize"
        #Option     "VBSize"
        #Option     "UseCCEfor2D"
        #Option     "PanelWidth"
        #Option     "PanelHeight"
        #Option     "UseFBDev"
	Identifier  "Card0"
	Driver      "r128"
	VendorName  "ATI"
	BoardName   "Rage 128 Mobility LF"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
 	DefaultDepth 24
	SubSection "Display"
		Depth     16
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes "1024x768"
	EndSubSection
EndSection

Section "DRI"
EndSection

```

After a little searching and reading from Wikipedia, I think the modeline is key here, and that it is specific to the display on the Inspiron 4000.  Someone having a similar issue on another computer might not want to copy that modeline but to find another one.

---

### Post by nc_jed on 2007-08-04
U da man, tictac...  I had all but given up hope on this beater laptop, but the additions in the first block worked a charm.  On top of that, xfce recognized the changes on reboot -- no manual intervention required...

BTW, are you really running full blown Ubuntu (with Gnome)?  I never even considered it on my 4000 (700Mhz).  U got some speed hacks to share?

Cheers,
NCJed


> **thetictacaddict said:**
> I was having the same problem on my Inspiron 4000, and I have just found the solution!  I found a "driver" RPM on Dell's website for RedHat 7, which turned out to contain an XFree86 config file.

Change your driver from "ati" to "r128",  and under your monitor section, add
```
HorizSync     31.5 - 48.5
VertRefresh   60
Modeline "1024x768"   65.000  1024 1048 1065 1344   768  770  776  806
```

At least that worked for me.  You may still need to change your resolution settings under XFCE (I had to in Gnome).

Here's the full config file from the RPM, in case it helps.
```
Section "ServerLayout"
	Identifier     "XFree86 Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
	Load  "pex5"
	Load  "record"
	Load  "xie"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "keyboard"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option      "Protocol" "PS/2"
	Option      "Device" "/dev/mouse"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
	HorizSync     31.5 - 48.5
	VertRefresh   60
	Modeline "1024x768"   65.000  1024 1048 1065 1344   768  770  776  806
EndSection

Section "Device"
	### Available Driver options are:-
        #Option     "NoAccel"
        #Option     "SWcursor"
        #Option     "HWcursor"
        #Option     "Dac6Bit"
        #Option     "Dac8Bit"
        #Option     "ForcePCIMode"
        #Option     "CCEPIOMode"
        #Option     "CCENoSecurity"
        #Option     "CCEusecTimeout"
        #Option     "AGPMode"
        #Option     "AGPSize"
        #Option     "RingSize"
        #Option     "VBListSize"
        #Option     "VBSize"
        #Option     "UseCCEfor2D"
        #Option     "PanelWidth"
        #Option     "PanelHeight"
        #Option     "UseFBDev"
	Identifier  "Card0"
	Driver      "r128"
	VendorName  "ATI"
	BoardName   "Rage 128 Mobility LF"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
 	DefaultDepth 24
	SubSection "Display"
		Depth     16
		Modes "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes "1024x768"
	EndSubSection
EndSection

Section "DRI"
EndSection

```

After a little searching and reading from Wikipedia, I think the modeline is key here, and that it is specific to the display on the Inspiron 4000.  Someone having a similar issue on another computer might not want to copy that modeline but to find another one.

---

### Post by SSmith on 2007-08-09
I don't think the modeline is the trouble, I think that is an older part of X, which you probably came across due to the age of the laptop.  If you stick with simply adding the correct horizsync and vertrefresh ranges (HorizSync 31.5-55 and VertRefresh 40-70) you be alright.

Section "Monitor"
   Identifier "Generic Monitor"
   Option "DPMS
   HorizSync 31.5-55
   VertRefresh 40-70
EndSection

Also, if you are using an ATI Rage M3, I'd suggest you drop the defaultdepth down to 16, you should see some performance improvement.

---

### Post by thetictacaddict on 2007-08-10
Man, I forgot to check up on this thread sooner.  Glad I could help, nc_jed!  Yes I was running regular Ubuntu with Gnome, but it was pretty slow and I'm doing a re-install right now with Xubuntu.  I've found that Gnome will actually run pretty well on older hardware if you have enough RAM (sometimes faster than xfce), but I've only got 128MB in this laptop.  It was swapping a lot.

I did try a few things to speed it up: I used Openbox instead of Metacity, mrxvt instead of gnome-terminal, Epiphany instead of Firefox, and told Nautilus not to manage the desktop.  I also tried turning off a few services but in the end it still ran slow so I decided to try Xubuntu on it.  I also ordered a 256mb stick of RAM :)

When I finish with the Xubuntu install I guess I'll have the same resolution issue.  SSmith, I'll try the sync and refresh lines first like you suggested.

---

### Post by smellydog on 2007-10-21
after much trial and error, i managed to get xubuntu 7.04 installed on the same computer... inspiron 4000.  This thread really helped in getting the resolution to look great, like it should.  All i did was change the settings as in the first block aslo and restarted the desktop and all was beautiful!

---

### Post by thetictacaddict on 2007-10-21
Good to hear it worked for you, smellydog.  I managed to get some RAM for my Inspiron 4000, and with 512MB, it passably runs regular Ubuntu Gutsy (no desktop effects, I'm afraid :)).  Gutsy detected the resolution fine, too.

---

### Post by smellydog on 2007-10-29
note to self, upgrade ram, install ubuntu gusty, got it!  I will definitely have to try that.  But from what i understood with the graphics card, it is 3d with shared memory?  and it still did not render the compiz graphics option properly?

---

### Post by thetictacaddict on 2007-10-29
Be forewarned, it is not exactly a speed demon.  Plus the Inspiron 4000 is kind of picky about RAM and the right kind can be sort of expensive. It totally runs though.  I was impressed.

I hadn't tried to get Compiz running (except for clicking "Normal" under effects) but I worked on it for a little while today, after seeing your post. I still couldn't get it working.  Let me know if you do, I'd like to see it try to run on this machine :p

---

### Post by nc_jed on 2007-10-29
In an attempt to turn this into an Inspiron 4000 end all be all post, check this site out for all your Inspiron 4000 gear: [http://www.adapturl.com/laptop-dell-inspiron-4000.html](http://www.adapturl.com/laptop-dell-inspiron-4000.html)

---

