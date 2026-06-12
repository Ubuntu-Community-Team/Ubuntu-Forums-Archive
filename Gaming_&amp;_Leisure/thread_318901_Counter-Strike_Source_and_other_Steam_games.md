---
title: "Counter-Strike Source and other Steam games"
date: 2006-12-14
forum: Gaming &amp; Leisure
---

### Post by Copperteeth on 2006-12-14
I got steam installed using this guide

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

CSS runs but i had to force it into dxlevel 7 to run, although i havent tried the newer dx levels, but anyway...

counterstrike runs, but i only get 10 - 15 frames per second, and on windows i get about 40 - 50, decent settings, on a radeon9600

i wasnt expecting to get good framerate with great settings but i extepected it to be playable...
any suggestions?

---

### Post by Fitzy_oz on 2006-12-14
> **Copperteeth said:**
> I got steam installed using this guide

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

CSS runs but i had to force it into dxlevel 7 to run, although i havent tried the newer dx levels, but anyway...
counterstrike runs, but i only get 10 - 15 frames per second, and on windows i get about 40 - 50, decent settings, on a radeon9600
i wasnt expecting to get good framerate with great settings but i extepected it to be playable...
any suggestions?

Which chipset? (RV350 A?) - What model is the card. 
Post your /etc/X11/xorg.conf file.  

I also have a 9600 (Chipset is RV350AQ - 9600SE), and have found no way around the poor 
performance or a way to get it to Directly Render 3d via openGL (Which WINE wraps for D3d).  
THe long and short of it is that ATI's driver doesn't support (or does a pretty sucky job of supporting) the 9600(RV350) in 3D.  I have been throgh almost every post and have yet to find a single post with settings that will make it work.
The thing that is most frustrating is that I have an old P4 1.6ghz with no DDR ram an an Nvidia Mx440 (really low end) 64mb video card that basically wipes the floor with the 1.8 gig athlon with the 128mb radeon and 1.5gi of ram - Crazy isn't it...

---

### Post by Copperteeth on 2006-12-14
Wow that sucks for you and me both brother... i think i might go to my local mom and pop computer store tomorrow and trade my 9600 for a nvidia 6600 gt with a little extra $$, ive never actully tried to game on linux before but i guess ati is a no go for this sort of thing...

So if i were to get a 6600gt are you saying that i will be able to run counterstrike on some decent settings? any idea how decent? my /etc/X11/xorg.conf tells me my videocard is the following

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

...sux to my vcard

---

### Post by Fitzy_oz on 2006-12-15
> **Copperteeth said:**
> Wow that sucks for you and me both brother... i think i might go to my local mom and pop computer store tomorrow and trade my 9600 for a nvidia 6600 gt with a little extra $$, ive never actully tried to game on linux before but i guess ati is a no go for this sort of thing...

So if i were to get a 6600gt are you saying that i will be able to run counterstrike on some decent settings? any idea how decent? my /etc/X11/xorg.conf tells me my videocard is the following

Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

...sux to my vcard


That would undoubtedly fix it yes.  As I say, my crappy Nvidia is doing ok and it's 5 years old.

You can try this config - 
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AQ [Radeon 9600 SE]"
	Driver "ati"
        BusID  "PCI:1:0:0"
        Option "DRI" "true"
        Option "ColorTiling" "on"
        Option "EnablePageFlip" "true"
        Option "AccelMethod" "XAA"
        Option "XAANoOffscreenPixmaps"
        Option "GARTSize" "64"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"


or
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AQ [Radeon 9600 SE]"
	Driver "ati"
        BusID  "PCI:1:0:0"
        Option "DRI" "true"
        Option "ColorTiling" "on"
        Option "EnablePageFlip" "true"
        Option "AccelMethod" "XAA"
        Option "XAANoOffscreenPixmaps"
        Option "GARTSize" "64"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "radeon"

Performance for me on both were shocking - I'm jumping ship to Nvidia.  i've had my fill of ATI's drivers on both platforms.

Good luck mate,  Let me know how you get on.

:)

---

### Post by Fitzy_oz on 2007-01-08
After weeks of messing about with the driver I have managed to get Direct 3d Rendering working for the 9600SE.  The problem appeared to be with Kernel Module.  Follow This Guide exactly (This is an extract from the unofficial wiki, it is important to note that only these steps worked for me, NOT, I repeat NOT the entire process"

*Download the ATI driver installer: ati-driver-installer-8.x.x.run (this installer is for 32bit and 64bit systems).

*Install the Tools
sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 linux-headers-$(uname -r)

*Create the install packages
bash ati-driver-installer-8.29.6.run --buildpkg Ubuntu/dapper

*Install the packages (Note: This is where the howto broke down for me)
sudo dpkg -i xorg-driver-fglrx_8.29.6-1_i386.deb -f
sudo dpkg -i fglrx-kernel-source_8.29.6-1_i386.deb -f
sudo dpkg -i fglrx-control_8.29.6-1_i386.deb -f 

*Remove any old Sources:
sudo rm /usr/src/fglrx-kernel*.deb

*Build and Install The module
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a

*Edit your xorg.conf and add the highlighted lines if they're not already there:

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
     [COLOR="Red"]   Load    "fglrx[/COLOR]
      [COLOR="Red"]  Load    "dri"[/COLOR]
        Load    "extmod"
        Load    "freetype"
[COLOR="Red"]        Load    "glx"[/COLOR]
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

ection "Device"
        Identifier      "Generic Video Card"
        Driver          [COLOR="Red"]"fglrx"[/COLOR]
        BusID           "PCI:1:0:0"

*Chances are you will need to add this line also:
[COLOR="Red"]Section "Extensions"
        Option "Composite" "Disable"
EndSection[/COLOR]

After you have completed these steps you should be able to reboot and check to see if the driver has initialized by typing #fglrxinfo in a terminal or glxinfo |more should return something like this:


OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600SE Generic
OpenGL version string: 2.0.6234 (8.32.5)


That's It,
May not work for everyone, but I'd tried just about everything else.

---

