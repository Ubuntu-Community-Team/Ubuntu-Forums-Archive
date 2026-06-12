---
title: "5 button mouse (or 7 if you like)"
date: 2006-09-15
forum: Desktop Environments
---

### Post by Mozzer on 2006-09-15
I'm looking to configure my mouse to get the side buttons to function like they do in Windows (i.e. Back and Forwards). I have read various bits and pieces on this and I tried telling xorg.conf that I have 7 buttons (left, right, middle click, scroll up, scroll down and the 2 side buttons). Then I set the ZAxisMapping to "6 7" but on a reboot this doesn't seemed to have worked (now my scroll wheel does Back/Forwards instead of scrolling).

Looking at this thread ( [http://ubuntuforums.org/showthread.php?t=77005](http://ubuntuforums.org/showthread.php?t=77005) ) I found xev which helps you analyse what buttons are being pressed.

Left click = 1
Middle click = 2
Right click = 3
Scroll up = 6
Scroll down = 7

The last two are since I tinkered with xorg.conf, they will probably go back to 4 and 5 when I reboot. The funny ones though are...

Left side button = 2
Right side button = 3

It seems that Ubuntu can't recognise the side buttons and tries to map them as other buttons. This means that when I use the left side button I get my scrolly thing in Firefox and when I use the right side button it opens the context menu.

I would be gratfeul if anyone could shed some light on what the problem is here; is some sort of button reconfiguration required?

By the way the mouse is a wireless Packard Bell, model number CO-5P.

Thanks,
Mozzer

---

### Post by Anduu on 2006-09-15
The mouse section of your xorg.conf should look like this:

```
Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Buttons" "7"
	Option "Protocol" "ExplorerPS/2"
	Option "ButtonMapping" "1 2 3 7 6"
	Option "ZAxisMapping" "4 5"
	Option "Resolution" "800"
#	Option "Emulate3Buttons" "true"
EndSection
```

---

### Post by Mozzer on 2006-09-16
This is what my mouse section looks like now:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
	Option 		"Buttons" 		"7"
	Option 		"ButtonMapping" 	"1 2 3 7 6"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

I'm assuming the resolution and the order in which the options appear doesn't matter. But what about the protocol? I thought I'd better not change that in case it was something specific to do with my hardware. Would changing it to "ExplorerPS/2" help at all? Currently my side buttons are still mapped as 2 and 3.

---

### Post by Anduu on 2006-09-16
Have you restarted?These changes won't take effect until you do.

I am not sure if the Imps/Explorer thing makes a difference or not.Try it and see.

4 and 5 in ZAxisMapping are supposed to be your scrollwheel.

1,2 and 3 are left,right and middle click.

6 and 7 are the side buttons which can be any order depending on which you want to be forward/back.

---

### Post by Mozzer on 2006-09-18
Yep, I've rebooted with those settings and all the buttons 1-5 are registering properly but it still logs the left side button as 2 (middle click) and the right side button as 3 (right click). Strange indeed...

---

### Post by boombox1387 on 2008-01-25
I hate to dig up a dead thread, but has this ever been resolved?  I'm having the same problem.  When I run xev:
Left Click = button 1
Middle Click = button 2
Right Click = button 3
Scroll up = button 4
Scroll down = button 5

but the problem:
Back Button = button 2
Forward Button = button 3

This means that editing xorg.conf doesn't work because Ubuntu doesn't recognize that my forward and back buttons are unique.

---

### Post by boombox1387 on 2008-01-25
Maybe I should have tried just a little bit harder before posting that.  Turns out changing the "Protocol" line in the xorg.conf file from "ImPS/2" to "ExplorerPS/2" and rebooting worked for me.  Thanks Anduu

---

### Post by Anduu on 2008-01-25
> **boombox1387 said:**
> Maybe I should have tried just a little bit harder before posting that.  Turns out changing the "Protocol" line in the xorg.conf file from "ImPS/2" to "ExplorerPS/2" and rebooting worked for me.  Thanks Anduu

Thats why they keep these old threads around ;)

---

### Post by pizzicar on 2008-01-26
The one big issue I still had with my Ubuntu install - solved! Thanks for letting me piggyback on your success and question. I had been searching posts for some time but there is so much older information out there that involves adding software that I just let it go. Thanks Anduu!

---

