---
title: "Compiz destroys my borders"
date: 2008-04-09
forum: Desktop Effects &amp; Customization
---

### Post by markcgriffiths on 2008-04-09
Hi,

I had my desktop settings working fine but then I installed the latest ATI drivers and it didn't work anymore.  I couldn't even get Compiz to be enabled.

I did this; then it was enabled,

change the path on the line that is for COMPIZ_BIN_PATH to "/usr/bin" instead of "/usr/local/bin"

Also, change the line that says:
COMPIZ_NAME="compiz"
to
COMPIZ_NAME="compiz.real"

Then my borders disappeared if I enabled the effects.  Anyone know why?  I have emerald installed.

---

### Post by markcgriffiths on 2008-04-09
Extra information:

mark@mark-laptop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
mark@mark-laptop:~$  LIBGL_DEBUG=verbose
mark@mark-laptop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
mark@mark-laptop:~$

---

### Post by Rinzwind on 2008-04-09
I've had this happen too and normally it means your driver is not properly installed. 

At the command prompt type
metacity --replace
to have the normal borders back without compiz.

Then you can check if it's indeed the driver.is

This: Xlib: extension "XFree86-DRI" missing on display ":1.0". is an errormessage.
Copy paste into google gives...

[http://ubuntuforums.org/showthread.php?t=199835](http://ubuntuforums.org/showthread.php?t=199835)
[http://www.linuxforums.org/forum/ubuntu-help/78492-extension-xfree86-dri-missing-display-1-0-a.html](http://www.linuxforums.org/forum/ubuntu-help/78492-extension-xfree86-dri-missing-display-1-0-a.html)
and a lot more ;)

---

### Post by russo.mic on 2008-04-09
did you try just running 

emerald --replace

from a terminal and look at output?

---

### Post by fela on 2008-04-09
run ```
gtk-window-border --replace
``` to get normal metacity on, but keeping the effects on also.

---

### Post by markcgriffiths on 2008-04-10
I tried this;

emerald --replace

metacity --replace

These commands didn't complete, I left them for about 30mins.  The screen flickered a little.

gtk-window-border --replace

I will try this when I get home.

---

### Post by markcgriffiths on 2008-04-10
That command did me no good either.

mark@mark-laptop:~$ gtk-window-border --replace
bash: gtk-window-border: command not found
mark@mark-laptop:~$ 


Trouble is, I'm too scared to reinstall my ATI driver as then I might not be able to watch movies on my external monitor as opposed to my laptop's.  Hence why I am in this mess.

---

### Post by Martje_001 on 2008-04-10
I think the command should be:
```
gtk-window-decorator --replace
```

---

### Post by markcgriffiths on 2008-04-10
gtk-window-decorator --replace

That didn't help, still no borders.

---

### Post by Therion on 2008-04-10
This will prevent Emerald from starting up and taking control over your Window Decorations when you start Compiz Fusion.  This means your Window Decorations will use whatever GTK theme you're using.  Compiz, Yes...  Emerald, No.

If you're okay with that, proceed to your Terminal:

```
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manager
```

---

### Post by POW R TOC H on 2008-04-10
Under System->Preferences->Advanced Desktop Effects Settings
turn on the option "Window decoration"
That should do it!

---

### Post by markcgriffiths on 2008-04-10
Under System->Preferences->Advanced Desktop Effects Settings
turn on the option "Window decoration"

Thanks, I tried that already, it has always been on.  I did have compiz working fine until I installed those latest drivers.  I also turned on XGL or something. After that my problems started.

If I disable emerald, what does it mean in practice? How easy is it to rollback if something screws up?

---

### Post by Therion on 2008-04-10
> **markcgriffiths said:**
> If I disable emerald, what does it mean in practice? 
It means you will not be able to use Emerald to decorate your Windows.  

If you're a big fan of Emerald themes, you won't want to do this (disable Emerald).  

If you don't use Emerald for theming your windows, go for it.

---

### Post by noirtier_de_villefort on 2008-04-10
"sudo nvidia-xconfig --add-argb-glx-visuals -d 24" should work... it did for me

---

### Post by markcgriffiths on 2008-04-11
"sudo nvidia-xconfig --add-argb-glx-visuals -d 24" should work... it did for me

I have an ATI mobility radeon card

---

### Post by russo.mic on 2008-04-11
is this because you have the latest ATI driver running AIGLX and you also have xserver-xgl installed?  I'm confused, do you have compiz working at all?  or is it just running without window borders?

Print out your xorg.conf and lets take a look.  
Russo

---

### Post by markcgriffiths on 2008-04-11
Well, you've probably guessed, I don't really know what I'm doing.  I had to install that AIGLX otherwise I couldn't play movies on my second monitor.  I can enable Compiz but those borders don't show, seems my computer runs slowly when it's turned on too.

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
	Fontpath	"/usr/share/X11/fonts/misc"
	Fontpath	"/usr/share/X11/fonts/cyrillic"
	Fontpath	"/usr/share/X11/fonts/100dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/75dpi/:unscaled"
	Fontpath	"/usr/share/X11/fonts/Type1"
	Fontpath	"/usr/share/X11/fonts/100dpi"
	Fontpath	"/usr/share/X11/fonts/75dpi"
	Fontpath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"type1"
	Load		"vbe"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"ATI Technologies Inc Radeon IGP 330M/340M/350M"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon IGP 330M/340M/350M"
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

---

### Post by markcgriffiths on 2008-04-11
mkdir -p ~/.config/compiz/ && echo USE_EMERALD="no" >> ~/.config/compiz/compiz-manage

That didn't work.  BTW I have completely uninstalled that ATI driver.

---

### Post by craftomaniac on 2008-04-12
Hello there. 

I have also had the same problem, but after reading lots and lots of posts from just about everywhere such that I cannot find them again, I managed to solve it. I had just tried using compiz and following guides, installed emerald, however it totally destroyed the window borders everytime i tried to run compiz. I read a post somewhere about using gtkwindowdecorator with compiz and tried it, got it working.

In Compiz Config Settings Manager, go to the Window Decoration plugin and enable it if it isn't already, then look for the "Window decorator to use" option or something like that, and type gtk-window-decorator --replace in it. That solved all my problems.

Pardon me if I sound like an idiot, I've only recently started using Ubuntu.

---

### Post by Unix_Slayer on 2008-05-03
Sorry for another stupid question, but I did an oops. I turned off the border on Kmix, and I can't seem to get it back. Anyone have a clue. New to X server, but have playing with Unix-Zenix, BSD, and Solaris for years at work. I never thought the Demon Bill would get me at home, but he did.


**_Never mind........_** Even a terminal programmer can work this x-server business. It's amazing. I see real dual NVidia 9600 GT OC Sli Color.

---

