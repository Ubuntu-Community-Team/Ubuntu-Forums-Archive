---
title: "Mapping buttons on Evoluent vertical mouse"
date: 2008-01-12
forum: Desktop Environments
---

### Post by zambizzi on 2008-01-12
Hi all,

I have an Evoluent Vertical Mouse 3.  I have pretty severe tendonitis in my right hand and bought this mouse to aide me in continuing work (programmer, 10 hrs. a day).

In Windows, the Evoluent drivers allow me to map specific functions to the mouse.  It has a thumb button, and an extra third button, (see attachment)

I need the buttons to map to what I have them set to do in Windows, I really hope this is somehow possible?  I use the thumb button as the wheel-click and the third (bottom) button on the other side as a double-click.  This helps so I can double-click variable values and other items while editing code.

Can this be done?

Here is my current mapping, which I found by searching the forums:

```
Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "Protocol" "auto"
	Option "Device" "/dev/input/mice"
	Option "Emulate3Buttons" "true"
	Option "Buttons" "5"
	Option "ZAxisMapping" "4 5"
	Option "ButtonMapping" "1 2 3 7 6"
EndSection
```

...however, this doesn't do what I need.

Any help would be much appreciated, thanks!!

---

### Post by zambizzi on 2008-01-16
Wow...really?  No one has any ideas?

---

### Post by taps on 2008-01-20
I have the same problem! Please help.

I use my Evoluent 2 as follows:
L=L
Mid=double click
R=R
Thumb=Back
Wheel button = wheel click

---

### Post by taps on 2008-02-12
Update: I have now managed to map my Evoluent as follows:

Left=Left
Middle=Forward
Right=Right
Thumb=Back
Wheel click=Open link in new tab (Firefox)
Still working on the wheel click as scroll wheel lock.

My xorg.conf file looks as follows:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
	Option		"ButtonMapping"		"1 2 7 3 6"
EndSection

```

---

### Post by zambizzi on 2008-02-12
Yeah, I didn't have a problem getting that far.  My question was more one of; "Can I make it do what it does in Windows?".

---

### Post by VinylPusher on 2008-02-28
This is excellent. My only problem with my Evoluent under Linux is that it seems to have lost somewhere in the region of 1000DPI in sensitivity when compared to Windows.

I have tried everything to get this working and I really cannot understand why it isn't.

I've changed the mouse driver to evdev in an attempt to fix it but that made no difference at all.

Adjusting Gnome's sensitivity options is an exercise in pointlessness. Not only are the "Acceleration" and "Sensitivity" options reversed, contrary to all reason or logic, but they are unwieldy in the extreme.

"xset m 1 1" from a terminal seems to be Linux's (not just Ubuntu's) sweet spot, where mouse movement maps linearly to pointer movement.

Mouse sensitivity and acceleration issues have plagued me for more than a decade under Linux. Why on Earth is this still an issue?

---

### Post by rob.webinator on 2008-06-06
How do I  tell xorg.conf what to do when Evoluent is not connected?
I used taps' xorg.conf settings and now my touchpad "right" button does not work.  Even better, is there a way to have both the Evoluent and built in touchpad buttons configured and working simultaneously?

---

### Post by reginak on 2008-06-15
Hi, I'm a brand-new Ubuntu user, and I also have the Evoluent vertical mouse. I don't use the scroll-lock button, but I do miss using the thumb button for "back" and the middle button for "double-click". Help?

Thanks,
Regina

---

### Post by Chianti on 2008-06-22
Hello reginak,

  I'm also a new Ubuntu user and I have the same mouse. I don't know if you have found already a solution...

You have to edit the xorg.conf. In the terminal:

```
sudo gedit /etc/X11/xorg.conf
```

I don't know about the double click functionality as I don't use it. I changed the values as **taps** is describing in [his post]("http://ubuntuforums.org/showpost.php?p=4316293&postcount=4") and after playing with the order of the button numbers

```
Option		"ButtonMapping"		"1 2 7 3 6"
```

I managed to map the buttons as I wanted.

 example "1 2 **3 7** 6"

Left=**Forward**
Middle=**Left**
Right=Right
Thumb=Back
Wheel click=Open link in new tab (Firefox)

---

### Post by reginak on 2008-07-06
Oops, Chianti, so sorry I didn't respond! I hadn't figured out about subscribing to threads, lost this one. I have been working off the instructions in this thread here, with partial success so far:

[http://ubuntuforums.org/showthread.php?t=787790](http://ubuntuforums.org/showthread.php?t=787790)

---

