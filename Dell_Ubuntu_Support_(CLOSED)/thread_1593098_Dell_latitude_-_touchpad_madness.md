---
title: "Dell latitude - touchpad madness"
date: 2010-10-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xeroxed_yeti on 2010-10-11
Hi everyone,

I am new to this forum and new to ubuntu. However I used linux for a long time but never experienced this mouse stuff ;)

I was quiet impressed that ubuntu works well after the installation if there was not this little touchpad madness...

At the moment I'm using an external mouse and every click works, but whenever clicking a mouse button on the laptop or even touch the touchpad only the window in front can be accessed. Moreover the mouse buttons (both: external mouse and buttons on laptop) won't work anymore and accessing the menu bar is not possible ...the pointer can still be moved.

I'm using Ubunutu 10.04 LTS - Lucid / Gnome 2.30.2 on a DELL latitude E6400.

I tried to figure out what mouse driver I used without success, and my xorg.conf is just filled with my graphic card stuff.

Are there any advices? 

Thanks

SOLVED: 

Have a look at /proc/bus/input/devices to verify your "mouse" input device - in my case AlpsPS/2 ALPS DualPoint TouchPad: 
 ```

I: Bus=0011 Vendor=0002 Product=0008 Version=0000
N: Name="DualPoint Stick"
P: Phys=isa0060/serio1/input1
S: Sysfs=/devices/platform/i8042/serio1/input/input14
U: Uniq=
H: Handlers=mouse1 event13 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0002 Product=0008 Version=6222
N: Name="AlpsPS/2 ALPS DualPoint TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input15
U: Uniq=
H: Handlers=mouse2 event14 
B: EV=f
B: KEY=420 70000 0 0 0 0
B: REL=3
B: ABS=1000003

I: Bus=0006 Vendor=001f Product=001f Version=0000
N: Name="Mouseemu virtual keyboard"
P: Phys=
S: Sysfs=/devices/virtual/input/input16
U: Uniq=
H: Handlers=rfkill kbd event15 
B: EV=100003
B: KEY=1ffffffffffff ffffffffffffffff ffffffffffffffff ffffffffffffffff

I: Bus=0006 Vendor=001f Product=001e Version=0000
N: Name="Mouseemu virtual mouse"
P: Phys=
S: Sysfs=/devices/virtual/input/input17
U: Uniq=
H: Handlers=mouse3 event16 
B: EV=7
B: KEY=420 70000 0 0 0 0
B: REL=103

```

Check if touchpad has been detected: xinput list 

```
  &#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS DualPoint TouchPad        	id=11	[slave  pointer  (2)]
&#9116;   &#8627; DualPoint Stick                         	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Mouseemu virtual mouse                  	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Dell BT Keyboard                        	id=17	[slave  pointer  (2)]
&#9116;   &#8627; Dell BT Mouse                           	id=18	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
   &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
   &#8627; Video Bus                               	id=6	[slave  keyboard (3)]
   &#8627; Power Button                            	id=7	[slave  keyboard (3)]
   &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
   &#8627; HID 413c:8157                           	id=9	[slave  keyboard (3)]
   &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
   &#8627; Dell WMI hotkeys                        	id=14	[slave  keyboard (3)]
   &#8627; Mouseemu virtual keyboard               	id=15	[slave  keyboard (3)]

``` 
Edit /usr/lib/X11/xorg.conf.d/10-synaptics.conf file:


```
  Section "InputClass"
 Identifier "touchpad catchall"
 MatchIsTouchpad "on"
 MatchDevicePath "/dev/input/event*"
 Driver "synaptics"
 Option "SHMConfig" "on"
 Option "TapButton2" "3"
 Option "VertEdgeScroll" "0"
 Option "HorizEdgeScroll" "0"
 Option "EmulateTwoFingerMinW" "5"
 Option "EmulateTwoFingerMinZ" "90"
 Option "VertTwoFingerScroll" "1"
 Option "HorizTwoFingerScroll" "1"
 Option "VertScrollDelta" "100"
 Option "HorizScrollDelta" "600"
 Option "CornerCoasting" "1"
 Option "CoastingSpeed" "100"
 Option "PalmDetect" "1"
 Option "PalmMinWidth" "7"
 Option "PalmMinZ" "90"
EndSection

```

---

### Post by mörgæs on 2010-10-11
Hi, welcome to the forum.

How does the touchpad work, if you boot a 10.10 live CD?

---

### Post by TerminalWhimsy on 2010-10-11
Same problem Ubuntu 10.04 Lucid Linux, Gnome 2.30.2, Dell Inspiron 1420. Tried outright disabling my touchpad, but I can't seem to find the controlling files to alter or disable them.

Tried:
xinput list

and then running:
xinput set-int-prop “PS/2 Generic Mouse” “Device Enabled” 14 0

but it did nothing. Also ran the same program with "Macintosh mouse button emulation" id=15 but that turned the click off for both touchpad and USB mouse.

Suggestions?

---

### Post by mörgæs on 2010-10-11
> **TerminalWhimsy said:**
> 
Suggestions?

Yes, see the post above.

---

### Post by Atlv011 on 2010-10-12
[FONT=Times New Roman]The next step, with the AppArmor profile for Firefox still in complain mode, start Firefox and perform "normal activities". Open and close Firefox, browse some web sites[/FONT]

---

### Post by hkphooey on 2010-10-12
Not sure if this helps but here is a script I wrote to toggle my Touchpad on and off. I have a Vostro 1400 with Ubuntu 10.04

```
DEVICE="AlpsPS/2 ALPS GlidePoint"

if xinput list-props "$DEVICE" | grep "Device Enabled" | grep 1$
then 
    echo ... Disabling
    xinput set-int-prop "$DEVICE" "Device Enabled" 8 0
else
    echo ... Enabling
    xinput set-int-prop "$DEVICE" "Device Enabled" 8 1
fi
```

The device name I got from doing an 
```
    xinput list
```

The PS/2 Genric mouse and the Mac emulation thing are there as well, but those are not the Touchpad.

---

### Post by mörgæs on 2010-10-12
Does this help?
[http://ubuntuforums.org/showthread.php?t=1594662](http://ubuntuforums.org/showthread.php?t=1594662)

---

### Post by jbrice on 2010-12-21
Deleted - posted here in error

---

