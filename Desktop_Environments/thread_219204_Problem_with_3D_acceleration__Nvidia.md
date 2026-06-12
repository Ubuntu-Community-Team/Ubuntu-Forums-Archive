---
title: "Problem with 3D acceleration / Nvidia"
date: 2006-07-19
forum: Desktop Environments
---

### Post by rpalyvoda on 2006-07-19
Hi,

I've been trying to get a 3D acceleration for my video card. I followed the method from ubuntu desktop guide
[https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html")

There is no error message, but when I do 
$ glxinfo | grep rendering

I get 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I've got a Nvidia GeForce 4 420 card on Toshiba Satelite laptop.

Please help!!!!!!!!!!!!!!!!!!!!!!!!!!!! Perhaps, someone has already encountered a similar problem....

Here is my xorg.conf file.

---

### Post by zxee on 2006-07-19
> Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 420 Go]"
	Driver		"nv"
	BusID		"PCI:1:0:0"

The sections in the xorg.txt you supplied that call for the "nv" driver are incorrect for loading the propriatary nvidia driver.
You should change "nv" to "nvidia". I don't know which driver you installed but the latest nvidia drivers usually update your xorg.conf for you unless you select not to do that. So try editing your working xorg.conf (back it up first) and see if that solves the problem.

---

### Post by rpalyvoda on 2006-07-19
Hi Xzee,

Thank you for your answer.

Unfortunately, each time I try to switch to nvidia driver, my xserver fails to load, and I have to come back to nv.

Is it because of my video card? I had the same problem before, when I got 3D on Ubuntu 5.10 and when I updated to 6.06.

But I don't know what to do to make it work rught now.

---

### Post by krismatth3 on 2006-07-19
Unfortunately "nv" is the open source "non accelerated" driver. You will not get 3d acceleration with this driver. You must switch to the "nvidia" driver.

When you say X fails to load, what happens? Can you paste the contents of any  /var/log/Xorg.log files?

---

### Post by jem7v on 2006-07-19
Different card, same problem. I'm using a GeForce2 MX 400 and I get the same error message when I try to get my acceleration going, but when I edit nv to nvidia I can't access the internet... I checked that log file you mentioned but it was empty. (Thus, I am also in need of assistance! But I'm going to keep looking for a solution myself... if I find it, I'll post it here, but it'd be swell if somebody stumbled across this and solved it for me to save my brain a headache!)

- b. ennis

---

### Post by goobers on 2006-07-19
when you switch to the nvidia driver, what message appears when the x server fails?

---

### Post by jem7v on 2006-07-19
I didn't get any message... my internet connection just didn't work the next time I started my computer, but when I changed it back to nv and rebooted it was fine.

---

### Post by tuxcantfly on 2006-07-19
first of all, I hope you have nvidia-glx installed, and have glx enabled under the modules section, and have dri and glcore disabled

as for the internet problem, try:

sudo /etc/init.d/networking stop
sudo /etc/init.d/udev stop
sudo /etc/init.d/udev start
sudo /etc/init.d/networking start

---

### Post by jem7v on 2006-07-19
Doot doot do, okay. So, um, I was following the installation guide in the official desktop help manual, and it really really wasn't working. I just tried using this method instead:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
Um, it works much better, which is to say that it works instead of not working. So rpalyvoda, try using that method instead of what they suggest in the official manual. I think it Might also have a specific notice regarding your video card, but it might be a different GeForce4 that they're mentioning.

When I saw his topic headline (something like "Latest NVidia Drivers") I thought he meant drivers for the latest chipsets... not the latest versions of All the NVidia drivers, which is why I didn't try his method the first time. Anyhow. Yup. Hope it works for you too!

---

### Post by palsyboy on 2006-07-20
I also recommend running:
```
sudo apt-get install nvidia-glx
sudo dpkg-reconfigure xserver-xorg
```
Nice and simple, at least for my old card.  Just make sure you know your monitor's refresh rates in case they aren't auto-detected.

---

### Post by rpalyvoda on 2006-07-20
Yeah, it worked!!!!!!!!

Finally, after a lot of searching in the forums, I found out that I needed too lonux-restricted-modules package. Having installed it, everything worked!
As a metter of fact, in Ubuntu Desktop Guide there is no mention about linux restricted modules....

Except that my screen resolution was limited to 969x768 only, so it left a large black line on my screen. I found the solution on 
[http://www.ubuntuforums.org/showthread.php?t=139264:](http://www.ubuntuforums.org/showthread.php?t=139264:)

> **OPaul said:**
> In your xorg.conf add the following under the Screen section. ```
    Option         "ExactModeTimingsDVI"   "TRUE"
    Option         "ModeValidation"   "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
```
and in the /etc/modprobe.d/options file add this.```
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1
```
I'm pretty sure that's all I needed to fix the problem. This information should be in the Notes section of the Howto (#8...eight, stupid smiley faces).

And thank you all for your help!!!!

---

### Post by 78charlesdarwin on 2008-03-17
Black bar problem with Nvidia drivers on a Geforce4 420 / 440 Go 16 / 32 Megabyte graphics card? Toshiba Satellite 1415? 14XX? I hear ya. The solution is found in these forums. I've summarized it here.

Here's something that worked for me (on a Toshiba Satellite 1415-S105):

[LIST]
[*]download [_[COLOR="Orange"]this custom EDID[/COLOR]_]("http://www.nvnews.net/vbulletin/attachment.php?attachmentid=24926&d=1175837051") (edid.bin.gz) by clicking the highlighted text.
[*]uncompress it to the directory: /etc/X11 (so:it is now "/etc/X11/edid.bin" - not "/etc/X11/edid.bin.gz") - you may need to be root or use "sudo" command to do this
```
#To open directory as root for easy drag-and-drop paste of file in Nautilus

sudo nautilus /etc/X11
```
[*]open your xorg.conf file (found in the directory: /etc/X11) in a text editor - you may need to be root  to do this. 
```
sudo gedit /edit/X11/xorg.conf
```
[*]add this line to the end of the section marked "Section "Device"" (make a new line and add it right before the "EndSection" line):

Option "CustomEDID" "DFP-0:/etc/X11/edid.bin"
 
that section should now look something like this:

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 420 Go]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	[COLOR="Lime"]Option		"CustomEDID" "DFP-0:/etc/X11/edid.bin"[/COLOR]
EndSection

(Don't mind the highlight color)
[*] save all your work
[*]close open applications
[*]restart your xserver by holding down the "CTRL", "ALT" and "Back Space" buttons at the same time
[/LIST]

when the login screen appears, you should notice that the black bar has already disappeared. Lucky You! 
Log in and you should find that the max resolution of 1024x768 has already been selected and applied for you.

Ubuntu 7.10
nvidia driver version: 1.0-9639
Geforce4 420 Go
Toshiba Satellite 1415-S105

my xorg.conf file is displayed below for your reference:
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
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation NV17 [GeForce4 420 Go]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
#	Option		"RenderAccel" "Off"
#	Option		"NoRenderExtension" "Off"
#	Option		"AllowGLXWithComposite" "Off"
	Option		"CustomEDID" "DFP-0:/etc/X11/edid.bin"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 420 Go]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

Check out this thread for more info.:
[http://www.nvnews.net/vbulletin/showthread.php?t=84773](http://www.nvnews.net/vbulletin/showthread.php?t=84773)
[COLOR="Red"][U]
For those of you that can't get into X[/U][/COLOR] (your GUI / Desktop), you might want to edit your xorg.conf file from the command prompt with a simple text editor such as vim. You would get X running again by changing ```
Driver     "nvidia"
``` to ```
Driver    "nv"
``` in  the "Section "Device"" section, saving, and starting X back up. This would allow you to download the edid.bin file and make the necessary changes with ease. You could also download Puppy OS, burn it to a CD, boot your computer off of that, mount your local HDD, download the edid.bin file, put it in /etc/X11 of the target drive and do the necessary text editing of your xorg.conf with Abiword (for example). In Puppy, you are already root, so permissions wouldn't be a problem.

---

### Post by jtuchscherer on 2008-05-23
Hi CharlesDarwin,

Thanks for this little Howto. It relieved me from quite some pain I had for a while on my Toshibe Satellite. It works like a charm now.

---

