---
title: "Lost mouse right click"
date: 2010-02-25
forum: Desktop Environments
---

### Post by the_nite_owl on 2010-02-25
Hi All.
After some recent software updates my mouse lost right click capability.
Can anyone direct me in how to re-enable right mouse button support?
I have had to modify the mouse settings in the past but cannot remember what file needs modifying or if there were specific entries for the right mouse button.

---

### Post by Kakers on 2010-02-25
Well im not sure this will help... but do you have your mouse listed in the /etc/X11/xorg.conf ?

This is what I have in that file:

```
Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

```

---

### Post by the_nite_owl on 2010-02-25
This is what I have.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Emulate3Buttons"	"true"
EndSection

A long time back I had issues with some mouse functions and had to edit a file, possibly xorg.conf.  It might have been related to the scroll wheel but I cannot remember for certain.  In any event there do not seem to be any special settings in my xorg.conf file now other than enabling 3 button support.  I guess I can try setting that to no and see what happens.

This all happended after the last round of software patches.  When it was done updating my mouse scroll wheel stopped working but I needed to reboot anyway and after I did the scrolling worked again.  It was a while before I noticed that the right mouse button no longer worked.
BTW, this is 8.04 Ubuntu.

I tried switching the mouse to left handed and when I did the left button would work to set focus to items but would not act to click on them.  The right button still did nothing.
I have to try digging up another mouse to see if it works but it seems too coincidental that it stopped right after the software updates.

---

### Post by Everybody Loves Hypnotoad on 2010-04-26
I am having a problem with the same symptoms, no right click-ability with my external mouse. But the laptop's built-in trackpad can still be used for right clicking. This is with Linux Mint 8 Helena with the latest patches as of today.

edit: Since there seem to be no xorg.conf in /etc/X11/ I can not post it's contents here.

edit 2: Seems like it was a hardware failure, the mouse was crying out for help by doing this and died later the same spring.

---

