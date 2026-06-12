---
title: "Mouse won't click unless (Shift &amp; Ctrl) is held down"
date: 2010-06-18
forum: Desktop Environments
---

### Post by prylux on 2010-06-18
I installed the Sugar (desktop environment) from the "Ubuntu software center" and the program said to capture the mouse you must press "Shift+Ctrl" and to release press "Shift+Ctrl".

Well I checked it out and after I closed Sugar I could not click on anything with the left mouse button and pressing the right mouse button brings up the "Window Menu". By accident I discovered that by holding "Shift+Ctrl" the mouse buttons work like they are supposed to...

Is there a way to reset the mouse?
I have tried another kernal and it did nothing
I am using 2.6.32-21 generic

I am using a Gigaware wireless usb mouse
and a touchpad

This is the output from "xinput list"

[INDENT]&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; HID 0a5c:4503                           	id=11	[slave  pointer  (2)]
&#9116;   &#8627; HID 062a:0000                           	id=12	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; HID 0a5c:4502                           	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)][/INDENT]

---

### Post by prylux on 2010-06-19
I also figured out some new behavior... 

Left clicking on the panel works but right clicking doesn't.
I have Avant Dock Bar and left clicking works but right clicking doesn't.
I can left click on the close window button and right clicking brings up the window menu...

I googled for help and most help said to go into Xorg.config but 10.04 doesn't seem to have that file anymore. :confused:

---

### Post by prylux on 2010-06-20
The solution to the problem was very simple

[INDENT]Click in the menu
 "System"
 "Preferences"
 "Windows"
Then under "Movement Key"
select the radio button for "super (or "Windows Logo")
[/INDENT]
I don't know if this is the way it is supposed to be set or if it is backwards now (I never looked at this setting before) but my mouse now works correctly...:popcorn:

---

