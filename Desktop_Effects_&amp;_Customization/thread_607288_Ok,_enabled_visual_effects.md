---
title: "Ok, enabled visual effects"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by xsabrewulf on 2007-11-08
I am getting very chopping performance on my X1900XT, AMD 2.6ghz 2GB ram. I get screen tearing when even scrolling down the forum... how come?


I dont know where all these eye candy features are... I right clicked on my desktop and went to the Visual effects tab then i clicked on "Extras" and it enabled... but im not sure where all these effects are?

---

### Post by xsabrewulf on 2007-11-08
nevermind I figured it out, had to install the compiz setting manager



another thing, how come the performance is SOOOOO slow?

every tears and its un bearable.

---

### Post by jimerickso on 2007-11-08
aiglx support is new so maybe next months release will be better.

---

### Post by xsabrewulf on 2007-11-08
Ever since i installed xserver or whatever it was called... everything went really slow...

Do i still need this installed for the desktop effects?

---

### Post by jimerickso on 2007-11-09
if you are using the 8.42.3 version of fglrx then you do not need xgl. if you are using anything else you will need xgl.

---

### Post by xsabrewulf on 2007-11-09
Yes, I am running the newest version of the drivers.

if I dont need xgl how do i uninstall it?

---

### Post by xsabrewulf on 2007-11-09
Ok i did

Sudo apt-get remove xserver-xgl


and i rebooted, it asked if wanted to use X settings or Gnome. I said X settings


and when I go back to desktop effects it says the old error about "the compsite extention is not available"

I thought i didnt need xserver with the new drivers?

sorry i am confused

---

### Post by jimerickso on 2007-11-09
this is probably because composite is set to zero in /etc/X11/xorg.conf. make sure composite is set to 1 (or enable) in /etc/X11/xorg.conf. it will be under the extensions section.

---

### Post by xsabrewulf on 2007-11-10
Ok i changed it to "1"

it says "disabled" just above the "1" but does that matter?

also, when i reboot ubunutu i get this prompt, what one should i choose?

[IMG]http://i3.photobucket.com/albums/y79/xsabrewulf/PC/Screenshot.png[/IMG]




i still get the extension error.


i get this error when i do compiz


[B][I]Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity [/I][/B]

I dont understand. I ahve my restricted drivers, I have the new ATI drivers. I uninstalled Xserver (which when I had it installed it worked, but i was getting HORRIBLE performance)

and I enabled the composite

---

### Post by xsabrewulf on 2007-11-10
now when I make changed to the file it says i dont have permissions..,

Man this Linux stuff has a lot to be learned.




```
Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
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
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Busid		"PCI:3:0:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x1440"	"1440x900"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Disable"
	Option		"Composite"	"1"
EndSection
```

---

### Post by Forlong on 2007-11-10
The latest driver from ATI is still buggy with AIGLX.
I'd recommend using the fglrx driver from the repos with Xgl. Not perfect but certainly better.

But to answer your question: yes, that does matter. You can't disable and enable Composite at the same time. If you still want to use the latest driver, remove the Disable part and as for the whitelist, see the last step [here](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support).

---

### Post by xsabrewulf on 2007-11-10
Ok, I did everything in that link that you provided.. I did everything from scratch.

I typed SKIP_CHECKS=yes compiz


and I got this:

```
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Then the screen flashed and I lost both my top and bottom bars.


and when i go to enable the desktop effects i just get the error "unable to enable desktop effects"

---

### Post by Ocxic on 2007-11-10
look through your compiz settings and make sure that "sync to vblank" options are all dysabled,, that option will degrade performance,, I always do

---

### Post by jimerickso on 2007-11-10
to get permission to change the file use:

sudo gedit /etc/X11/xorg.conf

change the "disable" to "enable".

when given the choice i usually choose "keep gnome settings" but its up to you.

---

### Post by xsabrewulf on 2007-11-11
the desktop effects dont enable at all, so im not worried about the performance.  I can only get the desktop effects to work if i install xserver and im trying to avoid that. grrrr i just want desktop effects:confused:

---

### Post by xsabrewulf on 2007-11-12
anymore advice?

---

### Post by xsabrewulf on 2007-11-14
last bump

---

