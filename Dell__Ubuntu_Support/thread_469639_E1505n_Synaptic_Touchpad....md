---
title: "E1505n Synaptic Touchpad..."
date: 2007-06-10
forum: Dell  Ubuntu Support
---

### Post by camarojones on 2007-06-10
Some of you may have noticed how sensitive the touchpad is on out laptops.
After digging for a bit, I found that there is a software fix to the tap and scroll sensitivity.

First off, you need to go to terminal, and run

```
sudo gedit /etc/X11/xorg.conf
```

Then look for:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

edit it with     Option	  "SHMConfig"   "on"    to look like this:

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"SHMConfig"       "on"
EndSection
```

(Mine does not require the use of the "on", but it doesn't hurt.)
Once you have edited the file, save it and exit the gedit program. Then run:

```
sudo apt-get install qsynaptics
```

This installs the GUI system for the synaptic trackpad
Once it is done, reboot the computer...a logout doesn't cut it here.
After the reboot, you can go into the terminal and type:

```
sudo synaptics
```

Adjust your trackpad as necessary.
The one problem I have found with this, is that the program needs to be ran everytime you log in. The way I got around it (will take sugestions if anyone knows a better way) was to:

System>Preferences>Sessions

I have 1 new program for disabling the tap-button, and 3 new ones for disabling the scroll.
They are as such:

NAME                                         **COMMAND**
Disable Tap-button                     **synclient Tapbutton1=0**
Scroll off                                      **synclient HScrollEmuOff=1**
Scroll off                                      **synclient VScrollEmuOff=1**
Scroll off                                      **synclient ScrollingMode=0**

(the formatting is not viewing correctly, but Disable Tap-Button and Scrolling off are the names...the command starts with synclient.)

I think that it may be possible to put these in the xorg.conf file under the trackpad section, but I haven't gotten around to trying it yet. But if you know that it can go there, please speak up.

I am sorry for how crude this is. After searching quite a few different sites and spending a bit getting it done, I figured I'd post it here to help out other folks that are new to Linux (like me), and want to learn new things.

Thomas

---

### Post by joedoro on 2007-06-10
Thanks so much for posting this! I have spent hours and hours trying to figure out how to turn tapping off with no success. I couldn't believe that there was not a simple solution.

For me I had to run sudo qsynaptics rather than synsptics

---

### Post by xyierz on 2007-06-10
You can add these options to the touchpad InputDevice section in xorg.conf, like this

Option "Tapbutton1" "0"
Option "HScrollEmuOff" "1"
Option "VScrollEmuOff" "1"
Option "ScrollingMode" "0"

If you're someone who actually uses the tap-to-click (like me), the default sensitivity is set way off. I've found that these options work well for me

Option "FingerLow" "32"
Option "FingerHigh" "45"

You can experiment with different values and settings with the synclient program.  See its man page and also the man page for synaptics for details.

Remove the gsynaptics package if you have it installed.  It hijacks all the settings you specify in xorg.conf, even the ones that are not configurable through its GUI.

---

### Post by camarojones on 2007-06-10
> **xyierz said:**
> You can add these options to the touchpad InputDevice section in xorg.conf, like this

Option "Tapbutton1" "0"
Option "HScrollEmuOff" "1"
Option "VScrollEmuOff" "1"
Option "ScrollingMode" "0"



Awesome. I appriciate that. Makes it MUCH easier to do then.

---

### Post by kerry_s on 2007-06-10
I'm using these settings for mine->

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"MaxTapTime"	"107"
	Option		"MaxTapMove"	"1"
	Option		"EmulateMidButtonTime"	"200"
	Option		"RBCornerButton"	"2"
	Option		"LockedDrags"	"true"
	Option		"EdgeMotionMaxSpeed"	"1"
EndSection
```

---

### Post by camarojones on 2007-06-10
**_UPDATE:_**

I ran into an error after I installed Beryl, and to make it work, the options have to be in the xorg.conf file...

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option		"VertScrollDelta"	"0"
	Option		"SHMConfig"		"on"
	Option		"Tapbutton1"		"0"
EndSection
```

I added

VertScrollDelta
Tapbutton1

and it stopped the tap and scrolling again.

---

### Post by Linicks on 2007-09-17
> **camarojones said:**
> 

Adjust your trackpad as necessary.
The one problem I have found with this, is that the program needs to be ran everytime you log in. The way I got around it (will take sugestions if anyone knows a better way) was to:

Thomas

Thanks for this post - I got qsynaptics and configured my pad exactly as I wanted :-)

As to saving the settings.  qsynaptics writes a file to $HOME/.qsynaptics

and all you need do is add:

qsynaptics -r

to /etc/rc.local to restore the settings when you log in.

Also, if you use firefox and have the horizonal scroll ON, in firefox goto about:config and set these keys to these values:

mousewheel.horizscroll.withnokey.action  0
mousewheel.horizscroll.withnokey.sysnumlines true

to stop the horizontal scroll making firefox jump through back<>forward history pages, but actually scroll the page if it is too wide.

Nick

---

### Post by Linicks on 2007-09-18
> **Linicks said:**
> 

As to saving the settings.  qsynaptics writes a file to $HOME/.qsynaptics

and all you need do is add:

qsynaptics -r

to /etc/rc.local to restore the settings when you log in.


Actually, that does'nt work - I don't know why?

But here is an easier way.  Run qsynaptics and set up your touchpad.  This will save the settings in $HOME/.qsynaptics as explained.

Then go:

System>Preferences>Sessions

and create a new 'startup' entry:

**Name**:  Qsynaptics - Configure Touchpad
**Command**:  qsynaptics -r

And save it.  Now when you log in, settings are applied correctly.

Nick

---

### Post by DouglasAWh on 2007-10-03
This is one of those things that should just be in System -> Preferences out of the box in my opinion.  Maybe in whatever is after Gutsy.  Thanks for the post though!  I've lost my IBM job application like 3 times now because of accidentally closing it with the touchpad, ugh!!!!!

---

### Post by Jasman on 2007-10-29
Does anyone know of a way to get your synaptics settings from a Windows installation to duplicate them in Linux? With my E1505, the touchpad sensitivity and action has never been good, and that's different from other laptops I've used. Somehow, Windows gets everything working the way I like it, but I can't duplicate it through xorg.conf. FWIW, I've been messing primarily with the FingerHigh and FingerLow settings, and I like my touchpad to be very sensitive and responsive.

---

### Post by app on 2007-11-01
How do I set the touchpad cursor speed? I have gsynaptics, but its "sensitivity" setting has no effect on cursor speed. IT IS TOO SLOW NOW and makes it almost impossible to use the machine without a mouse, and I hate mice. Especially when lying on a sofa or just having the damn machine on top of my LAP!

D620, Gutsy

---

### Post by bfriendly on 2007-11-07
I have a D820 and this has been driving me nuts. This did the sensitivity issue but how do you increase the speed of the mouse cursor using the touchpad? The speed setting only seems to effect the eraser head speed?

---

### Post by trwww on 2007-11-14
> **Jasman said:**
> Does anyone know of a way to get your synaptics settings from a Windows installation to duplicate them in Linux? With my E1505, the touchpad sensitivity and action has never been good, and that's different from other laptops I've used. Somehow, Windows gets everything working the way I like it, but I can't duplicate it through xorg.conf. FWIW, I've been messing primarily with the FingerHigh and FingerLow settings, and I like my touchpad to be very sensitive and responsive.

Hi Jasman,

I've been wanting to post these exact same sentiments. To be specific, I like everything about the touchpad except for the tap-to-click. I use it a lot and my E1505N just dosent get it.

I've used lots of laptops running windows. Lots. And every single one has behaved the way I "felt" it should. But I get lots of misses when when I tap-to-click on the E1505N. So far xyierz's comment in this thread has been the most accurate in describing what I need to do to get my touchpad like I want, but the misses when I tap-to-click is keeping me from ebaying my old machine.

If anyone could suggest what I need to do to make tap-to-click stop missing, I'd appreciate it.

Contrarily, horizontal and vertical scroll on the touchpad actually work on my E1505N, where I've never seen it work on a windows laptop.

trwww

---

### Post by geeree on 2007-11-15
> **camarojones said:**
> I am sorry for how crude this is. After searching quite a few different sites and spending a bit getting it done, I figured I'd post it here to help out other folks that are new to Linux (like me), and want to learn new things.

Thanks, Thomas. This looks interesting and I will try it on my Inspiron 640m. My touchpad has been bothering me lately —

[http://ubuntuforums.org/showthread.php?t=604457](http://ubuntuforums.org/showthread.php?t=604457)

Girish.

---

