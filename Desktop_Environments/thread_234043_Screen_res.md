---
title: "Screen res"
date: 2006-08-10
forum: Desktop Environments
---

### Post by Dylan103 on 2006-08-10
I just changed my parents comp to linux, and their screen res is really big, 800x600 and cant veiw full aps(setting up evolution for mail, cant see forward button), and in System > Prefs > Screen res  it ionly shows 800x600 but its capable of higher, how to fix it?

---

### Post by hopstah on 2006-08-10
```
sudo gedit /etc/X11/xorg.conf
```
scroll to the bottom and you will see a list of bit depths and resolutions.  ```
SubSection "Display"
     Depth     4
     Modes     "1280x1024".......
EndSubSection
```

add the resolution(s) you want to use to the 'Modes' line, in descending order from highest to lowest, and do ctrl+alt+backspace.  then you should be able to choose higher resolutions.

edit:  you need to add the resolutions to every bit depth section.  well, maybe you don't *have* to, but that's how it works best for me.

---

### Post by Dylan103 on 2006-08-10
And what does depth meen? do I have to keep adding stuff?

---

### Post by murataht on 2006-08-10
1) depth is the depth of the color. higher is the better...

2) above description is rather short. i try to expend it here.
   IMPORTANT: before editing the /etc/X11/xorg.conf file, you should make a backup of it. if x server didn't start after editing the xorg.conf, copy back the backup of xorg.conf and restart the x server. of course editing the xorg.conf, you should use "sudo gedit". 

a) maybe ubuntu did not detect your monitor type correctly. so i suggest first check your monitor type (maybe from google) and write down its specs: horzintal and vertical frequencies. with gedit open /etc/X11/xorg.conf, scroll down to the monitor section. if the frequencies are there, check if they are right, if there are no frequencies specified, add them yourself.

example:

Section "Monitor"
        Identifier      "iiyama sync master"
        HorizSync       30-110     #horzintal: add or correct this 
        VertRefresh     70-180     #vertical: add or correct this
        Option          "DPMS"
EndSection

b) after fixing the frequency, it is the screen section that is under the monitor section that you should edit.

you will find "subsection display" inside the screen section. here you should add the higher resolutions. i guess your original one maybe like this:

        SubSection "Display"
                Depth           1
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "800x600" "640x480"
        EndSubSection

and you should add the higher resolution before modes. maybe like this, but you have to choose the right resolusion for yourself:

        SubSection "Display"
                Depth           1
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection

(maybe 1280x1024 instead of "1280x768")

c) now. save these changes (make sure to have backup of xorg.conf), and kill the X server by ctrl+alt+backsapce. log in again, and check the system->preferences->screen resolution. hopefully the added ones are there.

good luck

---

### Post by Dylan103 on 2006-08-10
Ok,i tried editing before your post, it failed and im re-installing now, and if it fails, how would i get it back using the backup? and im going to copy your resolutions.

---

### Post by murataht on 2006-08-10
if the x does not restart with the edited xorg.conf, you do not have to reinstall the ubuntu. here is the simple backup solution.
 
1) copy the xorg.conf file to xorg.conf.backup
open a ternimal

>sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
(then you complete the edit and restart the x server)

2) if the X server fails to restart. go in to tty1:
ctrl+alt+F1 will get you into tty1. or ctrl+alt+F2 to tty2. ... tty6.
(tty7 for X server)

3) login with your account. (username password)

4) copy back the xorg.conf.backup to the xorg.conf.
 
>sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

5) now restart X:

>sudo gdm

---

### Post by srunni on 2006-08-10
Dylan, could you please post your entire xorg.conf file? Often, the graphics card driver that you're using is misconfigured, preventing your resolution from going above a certain amount (for me it was 1024x768). However, sometimes you may be able to just add in "1280x1024" or "1024x768" (whatever the monitor supports) and get it to work. The first time I tried, I somehow messed it up, and X didn't load, leaving me in terminal mode. However, if you back up your xorg.conf file like murataht said, it shouldn't be a problem. The second time, I did what seemed to be the same thing, and it worked. But don't be afraid to mess with the file, as long as you back it up first.

---

### Post by Dylan103 on 2006-08-10
Ok, tomorow I will, its not my computer and my parents are sleeping and i dont want to wake them up, but, when I do post it, could you edit it, and re-post?

---

### Post by murataht on 2006-08-11
then you should also post the hardware you got...
what monitor, what graphic card. and be specific as much as possible.

hope we can set it up for your parents.

---

### Post by Dylan103 on 2006-08-11
Ok, heres is my xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200 (RS480)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```


My monitor is a MAG Innovision 
Model Number : 700P

My graphics card is ATI Raedon Xpress 200 (I think)

---

### Post by Dylan103 on 2006-08-11
Anybody? Im getting in shit cause of this.

---

### Post by Greycloak on 2006-08-11
Try installing the 8.27.10 drivers from ATI.

[http://www.ubuntuforums.org/showthread.php?t=204910&highlight=8.27.10](http://www.ubuntuforums.org/showthread.php?t=204910&highlight=8.27.10)

---

### Post by murataht on 2006-08-11
for your monitor this is the specs:

Synchronization Range - Vertical 60 - 75 Hz
Synchronization Range - Horizontal 31 - 80 kHz 

before installing the driver from ati website. maybe you can try this to your xorg.conf file.

Section "Monitor"
        Identifier      "generic monitor"
        HorizSync       31-80 #this is the first line
        VertRefresh     60-75 #and this is the second line
        Option          "DPMS"
EndSection

just add those two lines as shown above. 

and the rest is fine, i think. cause you have all the resolution. 

hope this helps you. if this does not change anything, maybe you should change the graphic card driver from the link above. 

good luck.

---

