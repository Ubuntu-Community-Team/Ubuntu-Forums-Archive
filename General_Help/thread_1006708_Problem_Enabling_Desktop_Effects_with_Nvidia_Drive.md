---
title: "Problem Enabling Desktop Effects with Nvidia Driver 180.08"
date: 2008-12-09
forum: General Help
---

### Post by mysteriork on 2008-12-09
I am currently running Ubuntu 8.10 and I recently upgraded my Nvidia driver to 180.08 beta.  I have a Nvidia Geforce Go 7400 card.  The install went fine, but when I try to enable any form of desktop effects, the screen goes white and then displays vertical lines of either white lines or colored ones.  This does not go away and I am forced to restart.

Any advice about what I can do to fix this situation?!?

---

### Post by joethepirate on 2008-12-09
I'm having the same problem except I'm running a 7900gtx with the 177.80 driver. I think it might be related to the heat build-up.
Does anyone have any ideas?

---

### Post by gettinoriginal on 2008-12-09
Check this  :p

[http://meandubuntu.wordpress.com/2008/11/27/nvidia-18008-beta-drivers-out/](http://meandubuntu.wordpress.com/2008/11/27/nvidia-18008-beta-drivers-out/)

---

### Post by mysteriork on 2008-12-10
The problem for me is that once I enable desktop effects, I cannot do anything and I am forced to restart.  Also, compiz effects are already disabled...

---

### Post by Forlong on 2008-12-10
> **mysteriork said:**
> I recently upgraded my Nvidia driver to 180.08 [COLOR="Red"]beta[/COLOR]
Any particular reason for this?
If not, just revert back to the working driver.


P.S. desktop effects ARE compiz effects, see [http://forlong.blogage.de/entries/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710](http://forlong.blogage.de/entries/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710)

---

### Post by mysteriork on 2008-12-10
Well I upgraded because I was wonder the impression it would work *better* with compiz.  Previously I was having trouble with the window borders disappearing.  

I would like to revert back to my older driver, but when I try install one of the older drivers from the hardware drivers menu, it starts installing and then closes the installation and reverts back to the hardware drivers menu with nothing being changed.  

Do I have to actually uninstall the 180.08 driver.  IF so what do I need to do? What could be causing the installation of the older drivers to fail?

---

### Post by mysteriork on 2008-12-10
Here is a read out from the compiz check program, perhaps it can help...now when I try to enable desktop effects a window pops up saying desktop effects cannot be enabled...

```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation G72M [GeForce Go 7400] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

```

---

### Post by IceReaver75 on 2008-12-10
> **Forlong said:**
> Any particular reason for this?
If not, just revert back to the working driver.


P.S. desktop effects ARE compiz effects, see [http://forlong.blogage.de/entries/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710](http://forlong.blogage.de/entries/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710)

I was the one that suggested the update to the 180.06 drivers cause thats what fixed my nvidia 6200 card with the window border problems.  The driver states that it will fix the window border problems on the 6 and 7 series cards.  The directions for installing I listed were for the 180.06 32 bit driver which they installed but i found out later that they were running a 64 bit system.  I guess they installed the 64 bit driver over the top of the 32 bit driver without un-installing the 32 bit driver first.  So I suggested that maybe the 2 drivers are conflicting now but I wasn't to sure about that.  Could that possibly be the problem?

---

### Post by ushimitsudoki on 2008-12-10
180.06 and 180.08 are both to be avoided.

180.11 is good for me so far - been using it for several days. Multiple cards, multiple monitors, compiz, video, the works. There are some minor issues, but nothing making it unusable (unlike .06 and .08 ).

You *should* be able to install old over new, and new over old without any un-install in between. 

Finally, keep in mind the 180.xx series are still BETA - real "beta", not "Google Beta". There will be problems with them!

---

### Post by IceReaver75 on 2008-12-10
how do you install the 180.11 drivers?

---

### Post by ushimitsudoki on 2008-12-10
[180.11 (BETA) for Linux x86/x86-64 released]("http://www.nvnews.net/vbulletin/showthread.php?p=1861825"). 

[Installing NVIDIA Linux graphics drivers on recent distributions (FC, Ubuntu, etc)]("http://www.nvnews.net/vbulletin/showthread.php?t=72490")

They always [list the current drivers]("http://www.nvnews.net/vbulletin/showthread.php?t=122606").

Again, keep in mind the 180.xx series is in beta. I would suggest the latest stable drivers (177.82), unless they don't work for you, or you just like messing with new stuff. 

Edited to add:
Also, read the NVidia forums. Note there are a LOT of people having problems with the 180.xx series. So, don't be surprised if you have problems with them too.

---

### Post by IceReaver75 on 2008-12-11
Thank you for the info.  I was using the 180.06 drivers cause none of the nvidia drivers listed in hardware worked without window border problems.  So since I was already running the 180.06 driver I guess I'd try the 180.11 drivers.  Everything seems to be alright for now haven't had any problems yet.

Sorry to the tread starter for going off topic a little bit.  Just thought I'd ask here since it was brought up.

---

### Post by mysteriork on 2008-12-11
I actually decided to revert back to 177 at this point.  Now, the issue is I get the message "Desktop effects cannot be enabled."  I am not sure why that is considering they used to work with this older driver last week.  Here is a copy of my xorg.conf:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Sat Nov 15 11:14:51 PST 2008

Section "Monitor"
	Identifier     "Monitor0"
	VendorName     "Unknown"
	ModelName      "Unknown"
	HorizSync       28.0 - 33.0
	VertRefresh     43.0 - 72.0
	Option         "DPMS"
EndSection

Section "Screen"
	Identifier     "Screen0"
	Device         "Device0"
	Monitor        "Monitor0"
	Option         "AddARGBVisuals" "True"
	Option         "AddARGBLXVisuals" "True"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
	EndSubSection
EndSection

Section "Module"
	Load           "dbe"
	Load           "extmod"
	Load           "type1"
	Load           "freetype"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "InputDevice"
	Identifier     "Mouse0"
	Driver         "mouse"
	Option         "Protocol" "auto"
	Option         "Device" "/dev/psaux"
	Option         "Emulate3Buttons" "no"
	Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier     "Keyboard0"
	Driver         "kbd"
EndSection

Section "ServerLayout"
	Identifier     "Layout0"
	Screen      0  "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Device"
	Identifier     "Device0"
	Driver	"nvidia"
	VendorName     "NVIDIA Corporation"
	Option         "AddARGBVisuals" "True"
	Option         "AddARGBLXVisuals" "True"
	Option		"NoLogo"	"True"
EndSection

```

ALSO, when I try to install nvidia-glx through the package manager it says there is an error in the following output:

```

(Reading database ... 169142 files and directories currently installed.)
Unpacking nvidia-glx-173 (from .../nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/lib/nvidia/libglx.so.xserver-xorg-core' with
  different file `/usr/lib/xorg/modules/extensions/libglx.so', not allowed
dpkg: error processing /var/cache/apt/archives/nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by IceReaver75 on 2008-12-11
If you went back to the 177 driver wouldn't you want to install the nvidia-glx-177 package and not the nvidia-glx-173? 

from the error report it looks like the nvidia-glx-173 is trying to install.

---

### Post by mysteriork on 2008-12-11
> **IceReaver75 said:**
> If you went back to the 177 driver wouldn't you want to install the nvidia-glx-177 package and not the nvidia-glx-173? 

from the error report it looks like the nvidia-glx-173 is trying to install.

I actually went back to the 173 driver.  Either way, regardless of whether I try to install 173 or 177 I cannot install the glx file :P

---

### Post by IceReaver75 on 2008-12-11
did you try installing it through the terminal with the command:

sudo apt-get install nvidia-glx-173

that might tell you if possibly you are missing some dependicies at all

---

### Post by mysteriork on 2008-12-11
> **IceReaver75 said:**
> did you try installing it through the terminal with the command:

sudo apt-get install nvidia-glx-173

that might tell you if possibly you are missing some dependicies at all

I ran it in the terminal and I got the same output as above...What other nvidia packages do I need to install that this may be dependent on?!?  Maybe I have some nvidia package installed that is conflicting with the installation.

I have the following nvidia related packages installed:

nvidia-settings
nvidia-173-kernal-source
nvidia-common
nvidia-71-modaliases
nvidia-177-modaliases
nvidia-173-modaliases
nvidia-96-modaliases
xserver-xorg-video-nv

---

### Post by ellalan on 2008-12-11
Try uninstalling everything begins with "nvidia"in synaptics, install EnvyNG in synaptics. Then you'll finf EnvyNG under system tools and let it find the driver and install it for you.HTH.

---

### Post by mysteriork on 2008-12-11
> **ellalan said:**
> Try uninstalling everything begins with "nvidia"in synaptics, install EnvyNG in synaptics. Then you'll finf EnvyNG under system tools and let it find the driver and install it for you.HTH.

I just tried that and when I enable the driver in Envy and restart, desktop effects still won't work.  I go in to the package manager and the nvidia kernal is installed, but not the glx file.  If I try to install it now, I get this error:

(Reading database ... 169142 files and directories currently installed.)
Unpacking nvidia-glx-173 (from .../nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb) ...
dpkg-divert: rename involves overwriting `/usr/lib/nvidia/libglx.so.xserver-xorg-core' with
  different file `/usr/lib/xorg/modules/extensions/libglx.so', not allowed
dpkg: error processing /var/cache/apt/archives/nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-173_173.14.12-1-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by IceReaver75 on 2008-12-11
Looking up from others that have had this problem one way it was solved was to install

libgl1-mesa-glx 

before installing the nvidia-glx-173

---

### Post by mysteriork on 2008-12-11
> **IceReaver75 said:**
> Looking up from others that have had this problem one way it was solved was to install

libgl1-mesa-glx 

before installing the nvidia-glx-173

I already have that package installed.  If I uninstall it and then reinstall, it still does not work...

---

### Post by IceReaver75 on 2008-12-11
this is the only other thing i could find on the subject 

dpkg-divert --remove /usr/lib/libGL.so.1.2
aptitude remove libgl1-mesa-glx
aptitude install libgl1-mesa-glx
aptitude install nvidia-glx-173

but not sure about how that would work and i really don't want to mess something else up for you in the process but has worked for others

---

### Post by mysteriork on 2008-12-12
> **IceReaver75 said:**
> this is the only other thing i could find on the subject 

dpkg-divert --remove /usr/lib/libGL.so.1.2
aptitude remove libgl1-mesa-glx
aptitude install libgl1-mesa-glx
aptitude install nvidia-glx-173

but not sure about how that would work and i really don't want to mess something else up for you in the process but has worked for others

Do you have a link to this information?

---

### Post by IceReaver75 on 2008-12-12
I got this info from here what was listed as a bug report for this problem

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/257133](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/257133)

---

