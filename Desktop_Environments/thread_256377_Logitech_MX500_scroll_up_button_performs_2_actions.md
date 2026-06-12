---
title: "Logitech MX500 scroll up button performs 2 actions?"
date: 2006-09-12
forum: Desktop Environments
---

### Post by code-breaker on 2006-09-12
I'm installing an MX500 I just got. Here's the relevant section of my xorg.conf:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Device"		"/dev/input/mice"
	Option		"ZAxisMapping"		"4 5"
	Option 		"Buttons" "7"
	Option 		"ButtonMapping" "1 2 3 6 7"
EndSection
#	Option		"Emulate3Buttons"	"true"

The side buttons are working in Firefox (to move back and forth in the history). The scroll wheel is working, and the scroll-down button is working too. But for some reason, the scroll-up up button correctly scrolls up, and then Firefox steps back one page in the history. This button is doing two things. I confirmed this by running xev. Here is the output when I press the scroll-up button:

ButtonPress event, serial 29, synthetic NO, window 0x2800001,
    root 0x135, subw 0x0, time 2768406586, (174,172), root:(189,259),
    state 0x10, button 4, same_screen YES

ButtonPress event, serial 29, synthetic NO, window 0x2800001,
    root 0x135, subw 0x0, time 2768406586, (174,172), root:(189,259),
    state 0x810, button 6, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x2800001,
    root 0x135, subw 0x0, time 2768406586, (174,172), root:(189,259),
    state 0x810, button 4, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x2800001,
    root 0x135, subw 0x0, time 2768406722, (174,172), root:(189,259),
    state 0x10, button 6, same_screen YES

As you can see, button 4 then button 6 fire successively. What am I doing wrong?

---

### Post by wieman01 on 2006-09-13
There is a good howto on MX700/500, etc. Perhaps this helps:

[http://www.ubuntuforums.org/showthread.php?t=188302]("http://www.ubuntuforums.org/showthread.php?t=188302")

I have had tons of troubles with my Logitech mouse before I decided to buy myself a wired one and scrap the old one. But this thread offers help.

---

### Post by Zieher on 2006-09-13
Argh! I have the exact same problem on my MX900 (USB bluetooth) everything works fine, even the buttons are mapped correctly (the press of cruise up cruises up and jumps back one page](*,) )

All other posts refer to assigning keyboard inputs to buttonpress (release) events, but i have no idea how I'm to tell my mouse to do only one thing at a time... is there a different mouse protocol, maybe?

---

### Post by wieman01 on 2006-09-13
Hello Zieher, 

Follow the guide I have mentioned. Yes, this one is using an entirely different protocol. Should resolve your problems.

---

### Post by Zieher on 2006-09-14
Hi wieman,

thanks for the pointing. I had found that already, I seem to be consistent in making one mistake, i have been consequtively killing off X (Linux does have blue screens :) , thank goodness there is nano, because I'm am bad at backing up)
nonetheless, the problem persists, as there is always either a double action or same action on two buttons (cruise up and browser back). since my install is experimental anyways, I see this as exercise :-? 

what do you think about the new guide [http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)
?

---

### Post by Nemix77 on 2007-02-25
Having the exact same problem with my Logitech MX700 on PS/2 port.  The cruise up button does a double action, it cruises up then jumps one page back.  The new guide looks way too complicated, only want the cruise up button fixed.  Anyone?

---

### Post by Nemix77 on 2007-02-25
Sorry thought I found a solution.

---

### Post by Wayno-san on 2007-12-03
Sorry to resurrect this old thread but this problem still persists for me in Gutsy (7.10)... anyone find a solution?  The weird thing is that with the default setup the up button works but it doesn't do the double action...  I'm really glad to have the forward/backward buttons working though...

---

### Post by Hooya on 2008-04-23
This issue still exists in Hardy Heron.  Logitech MX Laser (MX1000) performs button 6 when cruise up is pressed, then button 8 when released.  6 is the proper button, but 8 is the back button.  Forward and Back (side buttons work properly from the get-go and cruise down only activates one event, but the issue remains for cruise up.

Also, the middle side button (which I would like to map seperately) is reporting button 2, so it's only possible for it to do whatever middle click is set to do.  Seems to be a related issue.

Side scroll buttons (tilt) aren't even registering in xev, but they do register in btnx when I use that program.  I can't get that program to actually do what it says it'll do though.

I suspect a driver issue.

By the way, the back in history doesn't effect things like the terminal, cruise functions normally there.  I guess you could get cruise to function normally in Firefox et. al. if you un-mapped the "back" button, but who wants to do that?

---

