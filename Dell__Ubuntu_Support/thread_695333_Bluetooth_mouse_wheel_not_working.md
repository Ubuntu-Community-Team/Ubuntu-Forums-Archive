---
title: "Bluetooth mouse wheel not working"
date: 2008-02-12
forum: Dell  Ubuntu Support
---

### Post by rienrien on 2008-02-12
I have a Dell XPS M1330 and a bluetooth mouse. Ubuntu finds the mouse all right automatically and the left and right buttons work. The wheel also works fine as the middle button, but the scrolling doesn't work at all.

When I use a normal USB mouse everything, including the scrolling, works fine. The touchpad also works as it's supposed to.

Here's the mouse portion of my xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

Any suggestions or ideas?

---

### Post by rienrien on 2008-02-25
*nudge*

---

### Post by Sandlst on 2008-02-27
Could you provide us with the make/model of your particular bluetooth mouse?  As a last resort, useful information is sometimes printed on the bottom of the mouse.

---

### Post by rienrien on 2008-02-27
> **Sandlst said:**
> Could you provide us with the make/model of your particular bluetooth mouse?  As a last resort, useful information is sometimes printed on the bottom of the mouse.
Yes, of course. It's a 5-button [Dell BT Travel Mouse]("http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&sku=310-9157"), though I suspect it  is actually a Logitech. I'm not sure if there's anything else that's needed?

Thanks!

---

### Post by raggari on 2008-02-27
> **rienrien said:**
> I have a Dell XPS M1330 and a bluetooth mouse. Ubuntu finds the mouse all right automatically and the left and right buttons work. The wheel also works fine as the middle button, but the scrolling doesn't work at all.

When I use a normal USB mouse everything, including the scrolling, works fine. The touchpad also works as it's supposed to.

Here's the mouse portion of my xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

Any suggestions or ideas?

My Dell BT Mouse config:

```

Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "CorePointer"
       Option          "Device"                "/dev/input/mice"
       Option          "Protocol"              "ExplorerPS/2"
       Option          "Buttons"               "7"
       Option          "ZAxisMapping"          "4 5"
       Option          "ButtonMapping"         "1 2 3 6 7"
       Option          "Emulate3Buttons"       "false"
EndSection

```

---

### Post by rienrien on 2008-03-03
> **raggari said:**
> My Dell BT Mouse config:
*snip*
That didn't work for me unfortunately :(

But I suppose there is something about the button mapping then, or the z axis mapping?

---

### Post by Tommy.Hudec on 2008-03-11
> **rienrien said:**
> That didn't work for me unfortunately :(

But I suppose there is something about the button mapping then, or the z axis mapping?

Hi, I'm successfully using this config:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option         "Emulate3Buttons"       "true"
EndSection

Moreover I setup mouse using xmodmap to remap buttons:
xmodmap -e 'pointer = 1 2 3 4 5 8 9 6 7'

---

### Post by rienrien on 2008-03-16
> **Tommy.Hudec said:**
> Moreover I setup mouse using xmodmap to remap buttons:
xmodmap -e 'pointer = 1 2 3 4 5 8 9 6 7'
Thanks. Unfortunately that didn't work either... 

Is there something I have to do to get the xmodmap change to work? 

I'm also a bit confused why there are 9 buttons to map when the mouse has 7. As I understand it, the wheel up and wheel down are supposed to be buttons 4 and 5, and I guess the back and forward buttons on the side are 6 and 7.

---

### Post by GordonFreeman on 2008-03-21
Hi,
I have the same mouse and for me your configurations don't work either, I can only use left,right and middle buttons.

rienrien, is your mouse working by now and if yes can you post your config?

---

### Post by GordonFreeman on 2008-03-23
My wheel is now scrolling, all I did was installing the bluez-utils package (sudo apt-get install bluez-utils) and then reconnected the mouse with "sudo hidd --search" and now I can scroll :)

---

### Post by RobertH on 2008-07-11
I hope this will will help you but my original problem was that the side scrolling buttons weren't working, not that the scroll wheel didn't work at all.

I have a Dell Bluetooth Travel Mouse ("D P/N PU705" written on the bottom of the mouse" I got it working with this config. First make sure imwheel is NOT installed. Then you need to run the command
```
cat /proc/bus/input/devices
```
Find our what number event it is. This is under "Handlers" in the "Dell BT Travel Mouse" section of the output of this command. My number was "event12"
Backup your /etc/X11/xorg.conf file (I suggest you time and date stamp your backup).
For example:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-9:13pm-12.7.08
```
Then go to your Configured Mouse section
I had:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"explorerPS/2"
	Option		"Buttons"	"9"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection
```
And you want to replace this with your new section using the evdev driver (making sure you use the appropriate device name) - you have to use the event one, not the mouse one!
In my case (M1530 & Dell BT Travel Mouse Dell Part Number PU705 [written underneath after "D P/N"]) This is my new mouse section:
```
Section "InputDevice"
	Identifier "evdev Mouse"
	Driver 		"evdev"
	Option 		"Name" "Dell BT Travel Mouse"
	Option          "evBits"  "+1-2"
	Option          "keyBits" "~272-287"
	Option          "relBits" "~0-2 ~6 ~8"
	Option          "Pass"    "3"
	Option 		"CorePointer"
	Option 		"Device" "/dev/input/event12"
	Option 		"Protocol" "ExplorerPS/2"
	Option 		"ZAxisMapping" "4 5"
	Option 		"WAxisMapping" "8 9"
	Option 		"Emulate3Buttons" "true"
	Option 		"Buttons" "9"
EndSection
```
There are a few important points before you go and restart X in your newfound glee. You have to do a couple more edits to your xorg.conf file.
You need to go down to the "ServerLayout" section
(Mine originally looked like this)
```
Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse" "Corepointer"
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
```
And change the line that refers to the "Configured Mouse". Since we changed the identifier of this to "evdev Mouse" we need to change it down here too or else X will not start properly :(, so mine became this:
```
Section "ServerLayout"
	Identifier	"Default Layout"
  	screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"evdev Mouse" "CorePointer"
	Inputdevice	"Synaptics Touchpad"
EndSection
```
(I removed all the Wacom tablet stuff in my xorg.conf becuase I don't have, or plan on buying, a Wacom tablet. You don't need to: It just was ticking me off ;))

I think it would be possible to just add the "evdev Mouse" section instead of replacing the "Configured Mouse" section and add the line above without deleting the old one, but I only use my touchpad and this Dell BT mouse so I haven't tried it. I chose to replace it so that my BT mouse is always using the right driver (I have heard that after suspends and stuff the mouse might come back using a different driver if there is another section left that might also work)
There is a bug with the evdev drivers that means that the DGA extension does not work properly. I don't know what the extension is or does but without this fix the cursor will jump around the screen in fullscreen OpenGL/SDL apps such as games. (The whole reason I wanted all my buttons working was for Enemy Territory: Quake Wars) so you have to disable it in you xorg.conf (or u can fix the problem in some games using a runtime option that you can find through a Google search) but this seems to fix it for all programs.

Go down to the "Module" Section.
Mine looked like this:
```
Section "Module"
	Load		"glx"
EndSection
```

And add in the line to disable the DGA extension
Tada:
```
Section "Module"
	Load		"glx"
        SubSection  "extmod"
             Option    "omit xfree86-dga"   # don't initialise the DGA extension
        EndSubSection
EndSection
```

When you go to restart X, I suggest that you logout and switch to Virtual Terminal 1 (Ctrl + Alt + F1) and login here. Then kill gdm:
```
sudo pkill gdm
```
and then start x manually:
```
startx
```
This way you can easily make the changes using gedit and then when u need to test them you can kill X (Ctrl + Alt + Backspace) (or logout if you're feeling patient) and restart X by running:
```
startx
```
again. 
The reason I recommend this way is because you get command line feedback if X doesn't start properly and you don't get that annoying failsafe X that rewrites all of you settings for fun :). And if you can't fix the problem from the command line feedback you just copy back one of your your backup files (because you *did* make them this time, didn't you?) :p and you are no worse off than when you started.

If you need to restore your original xorg.conf file just use the cp command.
For example:
```
sudo cp /etc/X11/xorg.conf-9:13pm-12.7.08 /etc/X11/xorg.conf
```

I will copy in my final xorg.conf and attach the before and after xorg.conf file for you to look at. Just remember that we have different laptops with different screens and graphics cards so just copy the input sections. My xorg.conf file also has a good example (good for me at least) of the touchpad configurations section if you are interested.

If you have been playing around with xmodmap just set everything back to their original defaults.

It is quite late at night for me now so if you think something I have written doesn't look quite right ask me or someone about it tomorrow.

These are the links I used to do this:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Mouse+Buttons")
[http://wiki.archlinux.org/index.php/Get_All_Mouse_Buttons_Working#Installing_the_evdev_Drivers]("http://wiki.archlinux.org/index.php/Get_All_Mouse_Buttons_Working#Installing_the_evdev_Drivers")

Good Luck and remember that you can always switch over to a Virtual Terminal and copy back your old config if something goes wrong.

EDIT- Sometimes the mouse will connect as a different mouse and event #. With this configuration this means that the mouse will not work. The device option in the xorg.conf has to be correct. It is supposed to be possible for evdev to corectly find the mouse (or you can use the /dev/input/by-id/ entries) but I have not had any luck in getting these to work. Maybe you can duplicate the section with a different identifier and a different device name if your mouse always seems to be one of two device locations. If you do this you will have to add the "InputDevice" line in the "ServerLayout" section for the new input device - Goodluck

Final xorg.conf file:
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

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600M GT]"
	Monitor		"Generic Monitor"
	SubSection "Display"
		Modes		"1440x1440"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GT]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"TripleBuffer"	"True"# Experimental
	Option		"BackingStore"	"True"# Experimental
	Option		"AddARGBVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"OnDemandVBlankInterrupts"	"true"
	Option		"CoolBits"	"1"
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
	Identifier "evdev Mouse"
	Driver 		"evdev"
	Option 		"Name" "Dell BT Travel Mouse"
	Option          "evBits"  "+1-2"
	Option          "keyBits" "~272-287"
	Option          "relBits" "~0-2 ~6 ~8"
	Option          "Pass"    "3"
	Option 		"CorePointer"
	Option 		"Device" "/dev/input/event12"
	Option 		"Protocol" "ExplorerPS/2"
	Option 		"ZAxisMapping" "4 5"
	Option 		"WAxisMapping" "8 9"
	Option 		"Emulate3Buttons" "true"
	Option 		"Buttons" "9"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"LeftEdge"	"120"
	Option		"RightEdge"	"830"
	Option		"TopEdge"	"120"
	Option		"BottomEdge"	"650"
	Option		"FingerLow"	"14"
	Option		"FingerHigh"	"15"
	Option		"MaxTapTime"	"180"
	Option		"MaxTapMove"	"110"
	Option		"ClickTime"	"0"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"0"
	Option		"MinSpeed"	"0.6"
	Option		"MaxSpeed"	"0.8"
	Option		"AccelFactor"	"0.080"
	Option		"EdgeMotionMinSpeed"	"200"
	Option		"EdgeMotionMaxSpeed"	"200"
	Option		"UpDownScrolling"	"1"
	Option		"CircularScrolling"	"0"
	Option		"SHMConfig"	"true"
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
  	screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"evdev Mouse" "CorePointer"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
        SubSection  "extmod"
             Option    "omit xfree86-dga"   # don't initialise the DGA extension
        EndSubSection
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-72
	Vertrefresh	43-60
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


```

---

