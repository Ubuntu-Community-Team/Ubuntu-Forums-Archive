---
title: "xorg mouse (wacom tablet) sometimes doesnt click"
date: 2009-04-22
forum: General Help
---

### Post by Mikebgr on 2009-04-22
Problem is that the mouse misses some clicks. Its not due to the mouse "dying", since it works flawlessly on my windows partition. I have a wacom tablet, and I have edited my xorg.conf accordingly to the faq to get the mouse working.

When I say misses some clicks i mean that if I click 5 times in a row, about 4 of the clicks will be counted on screen. (Sometimes I double click and it only shows like one click, sometimes I click and its as if I havent clicked at all)

Its not a major problem, but it get annoying very fast!

---

### Post by Favux on 2009-04-22
Hi Mikebgr,

It's good that you've ruled out a hardware problem in your Wacom mouse.

To help we need to know some things.  What version of Ubuntu are you using?  Which version of linuxwacom drivers and tools do you have?  How did you install them?  Which Wacom graphics tablet?  And we need to see a copy of your xorg.conf.

To know the Wacom sections we need to know what your tablet has.  They would be stylus, eraser, cursor (for the mouse), and pad (for the buttons on the tablet).

---

### Post by Mikebgr on 2009-04-23
```

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
#  Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

# Uncomment the following section if you you have a TabletPC that supports touch
# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "touch"
#  Option        "Device"        "/dev/ttyS0"       # SERIAL ONLY
#  Option        "Device"        "/dev/input/wacom" # USB ONLY
#  Option        "Type"          "touch"
#  Option        "ForceDevice"   "ISDV4"            # Serial Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
# EndSection

Section "ServerLayout"
  Identifier    "Default Layout"
  Screen        "Default Screen"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
  InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
#  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
# InputDevice   "touch"   "SendCoreEvents" # Only a few TabletPCs support this type
EndSection

```this was my xorg.conf file. I'm using Ubuntu 8.10 with the latest wacom and wacom tools drivers (Installed through apt-get, but I cannot tell exactly what version they are, how can I check that?). My tablet is CTE-430 (Sapphire), which has a pen (stylus and eraser) and a mouse (cursor).

On a sidenote:

```
mike@math:~$ xsetpointer -l
0: "Virtual core keyboard"    [XKeyboard]
1: "Virtual core pointer"    [XPointer]
2: "stylus"    [XExtensionKeyboard]
3: "eraser"    [XExtensionKeyboard]
4: "cursor"    [XExtensionKeyboard]
5: "Macintosh mouse button emulation"    [XExtensionPointer]
6: "AT Translated Set 2 keyboard"    [XExtensionKeyboard]
7: "Wacom Graphire3"    [XExtensionKeyboard]
```But I cant change the pointer to cursor manualy, I get this:

```
mike@math:~$ xsetpointer "cursor"
Extended device cursor not found
```Even if I try it without quotes, or using device #, etc. I thought skipping the virtual pointer and going directly to cursor would help =/

Thanks for the attention!

---

### Post by Favux on 2009-04-23
Hi Mikebgr,

You should be able to find the version by searching Wacom in Synaptic Package Manager.  You probably have linuxwacom 0.8.1-4 which is the Intrepid default.  You probably should update to 0.8.1-6 using the debs near the top of the Wacom wiki here:  [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)  Under the Intrepid section under Download the updated packages.  Download both packages for your CPU type on your desktop.  Double click to install.  Always make sure the Wacom drivers and wacom-tools are the same version.

I'll look at your xorg.conf.

---

### Post by Favux on 2009-04-23
OK, its a usb tablet.  It doesn't seem to have Wacom express keys, a cluster of buttons and one or more sliders on the tablet.  Or does it?  If it doesn't then you wouldn't need "pad".  Are there buttons on your stylus?  How many?  I can't tell from the Wacom site.

---

### Post by Mikebgr on 2009-04-27
Hello favux (with some delay)! You're right, I dont need pad, thats why I quoted it out on serverlayout, and its not being used. My stylus has 2 buttons (one for each click), and my version is  0.8.2.2-0 after I upgraded today to 9.04 !

Problem still occurs though =/

---

### Post by Mikebgr on 2009-05-30
any ideas on this one? I still have the problem...

---

### Post by Favux on 2009-05-30
Hi Mikebgr,

Same problem in Jaunty?  Hmmm.

Are you able to use "wacomcpl"?

---

### Post by matmat07 on 2009-05-31
I have the same problem, but I installed jaunty and it came with the problem. In fact it's mint 7 but it's based on jaunty. My wacom mouse is also working great on windows, and my integrated laptop mouse works as it should. The stylus is also well. 

Wacomcpl doesn't seem to work or even exist on my installation.

Edit: purging wacom-tool and xserver-xorg-input-wacom solved that issue, but it caused another bug with the stylus

---

### Post by Favux on 2009-05-31
Hi matmat07 and Mikebgr,

To use "wacomcpl" the output of:
```
xsetwacom list
```
should return stylus, eraser, cursor, pad.  If it is blank then:
```
xinput --list
```
will show you the names HAL is returning for your wacom devices.  matmat07 is yours a usb tablet too?

---

### Post by matmat07 on 2009-06-01
Yes it is usb

xinput --list returned that:
```
"Wacom BambooFun 4x5"	id=5	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14760
		Resolution is 10000
	Axis 1 :
		Min_value is 0
		Max_value is 9225
		Resolution is 10000

```
That was when I installed it(it was uninstalled to make the mouse work). I restarted the computer and here's the new output:
```
"Wacom BambooFun 4x5"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14760
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9225
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 511
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom BambooFun 4x5 pad"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 4
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14760
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9225
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 511
		Resolution is 1
	Axis 3 :
		Min_value is 0
		Max_value is 0
		Resolution is 1
	Axis 4 :
		Min_value is 0
		Max_value is 0
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 71
		Resolution is 1
"Wacom BambooFun 4x5 cursor"	id=7	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14760
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9225
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 511
		Resolution is 1
	Axis 3 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
	Axis 4 :
		Min_value is -1023
		Max_value is 1023
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom BambooFun 4x5 eraser"	id=8	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14760
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9225
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 511
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1

```

---

### Post by Favux on 2009-06-01
Hi matmat07,

OK, you can see that HAL and the default .fdi are not returning the linuxwacom names like stylus, eraser, cursor, and pad.  That's why xsetwacom commands and wacomcpl don't work.

For example for stylus you are getting:
```
"Wacom BambooFun 4x5"
```

So you can rename everything or translate everything as in Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)

Or you can use a modified 10-wacom.fdi that parses the names correctly.  It's at post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  They also talk about renaming things on this Wacom thread.

Then once "xsetwacom list" and "xinput --list" show the same names you should be able to use wacomcpl.  That's described in Section 3 on the first link above.  Hopefully that will fix the mouse.  If not you'll have to play with the settings.

This site gives you some more information on the settings:  [http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom](http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom)  And I am thinking you may have to try something with:
```
Suppress      integer (0 - 100)        number of data trimmed for the tools associated 
					  with the same tablet.

```
Be careful and keep a record of your defaults before you modify anything.

Good luck!

---

### Post by matmat07 on 2009-06-02
There's some improvement, I'll have to test for a while to see if it was the right setting to play with.

EDIT:so far "xsetwacom set cursor suppress 15" seem to work the best. If someone reads this also looks at the previous post's links for a way to make it permanant.

---

