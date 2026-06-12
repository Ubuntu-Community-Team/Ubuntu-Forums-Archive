---
title: "[SOLVED] Need to turn off tapping on Alps touchpad"
date: 2008-06-13
forum: Desktop Environments
---

### Post by portlandor on 2008-06-13
Hi,

I need to turn off tapping and scrolling on my Alps touchpad for a Sony VAIO SZ460.   Its gotten very irritating and making the touchpad.

Here is part of my xorg.conf-  I copied most of it from the example in /usr/share/doc

Section "InputDevice"
  Identifier	"Synaptics Touchpad"

  Driver	"synaptics"
  Option	"Device"		"/dev/psaux"
  Option	"Protocol"		"auto-dev"
# enable SHMConfig if you want to enable synclient
# NB: enabling SHMConfig is insecure, since any user can invoke it
#  Option	 "SHMConfig"		 "on"
  Option	"LeftEdge"		"120"
  Option	"RightEdge"		"830"
  Option	"TopEdge"		"120"
  Option	"BottomEdge"		"650"
  Option	"FingerLow"		"14"
  Option	"FingerHigh"		"15"
  Option	"MaxTapTime"		"180"
  Option	"MaxTapMove"		"110"
  Option	"EmulateMidButtonTime"	"75"
  Option	"VertScrollDelta"	"20"
  Option	"HorizScrollDelta"	"20"
  Option	"CornerCoasting"	"1"
  Option	"CoastingSpeed"		"3"
  Option	"MinSpeed"		"0.3"
  Option	"MaxSpeed"		"0.75"
  Option	"AccelFactor"		"0.015"
  Option	"EdgeMotionMinSpeed"	"200"
  Option	"EdgeMotionMaxSpeed"	"200"
  Option	"UpDownScrolling"	"0"
  Option	"CircularScrolling"	"0"
  Option	"CircScrollDelta"	"0.1"
  Option	"CircScrollTrigger"	"2"

EndSection

---

### Post by NilsE on 2008-06-13
Have you tried the mouse preferences under system > preferences?

---

### Post by portlandor on 2008-06-13
Hi,

Yes, just about every combination of settings but nothing works.  Its probably because it is not really a mouse I guess.

Now there is a spot in the middle of the pad which operates normally.  I think that somehow I have to figure out how to reduce the scrolling and tapping area to 0.  You can kind of see from the xorg.config snippet that there are lots of variables related to that, but I have no clue what they do.  I'm afraid to experiment as I might make it even worse.

Once I accidentally got the mouse moving so fast I couldn't see it.  I remember the old Star Trek episode where Kirk somehow starts moving so fast that he sounds like a bee and no one can see him, haha.

Rob.

---

### Post by NilsE on 2008-06-13
Are you not seeing the touchpad tab in the mouse properties.  Granted I have different hardware and am on Ubuntu not kunbuntu but mine does control most aspects of my touchpad. There is also very little other that the generic stuff in my xorg.conf file.

---

### Post by portlandor on 2008-06-14
Here's how I did it:

went to /usr/share/doc/xserver-xorg-input-synaptics/

copied the xorg.conf section out of the file: README.alps and pasted it into my /etc/X11/xorg.conf file under the "Input Device" section.

Removed "Identifier" line as it already was in my old file.

Uncommented  #  Option    "SHMconfig"     "on"

Set Option "Cornercoasting"   "0" to turn it off

Set Options "TopEdge" and "LeftEge" to "0"

Installed "synclient"   gave the command "synclient -m 1 | less"

Found the largest values in the output for x and y.

Used those for Options "BottomEdge" and "RightEdge"  (y=bottom, x=right)

That used up all of my touchpad space for just moving the cursor and nothing else, so now I have no more weird problems.

---

