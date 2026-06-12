---
title: "wacom tablet + xinerama"
date: 2009-06-24
forum: Desktop Environments
---

### Post by aris020 on 2009-06-24
I have been struggling with getting my Wacom Bamboo work with dual screen on fglrx with Xinerama (getting Xinerama work on fglrx is a different story, and a long one at that). 

Two problems I have encountered:

1. The cursor would only cover half of each screen. As I move from left to right, the cursor would jump from the middle of the left screen to the middle of the right screen, and vice versa. The remedy I found was to restrict the device to just one screen with 

> xsetwacom set stylus Screen_No 1

Alternatively, set same option in xorg.conf:

Section "InputDevice"
	Driver "wacom"
	Identifier "stylus"
	Option "Device" "/dev/input/wacom"
	Option "Type" "stylus"
	Option "ScreenNo" "1"
EndSection

(corresponding Wacom devices also have to added to Server layout section)
 
I have not found the way to use my tablet on both screens simultaneously.

Another problem is offset with gtk+ drawing programs such as gimp and inkscape. They have an offset between the drawing pen and the screen cursor. I have found [this fix for gtk 2.12.11]("http://archives.free.net.ph/message/20081118.061808.04d510b4.en.html"):

(did not yet figure out how to safely apply it). The problem still persists in my jaunty gtk 2.20 :(

---

### Post by Favux on 2009-06-24
Hi aris020,

This thread might have some useful info. for you.  You might want to start with post #61 here:  [http://ubuntuforums.org/showthread.php?t=1035029&page=7](http://ubuntuforums.org/showthread.php?t=1035029&page=7)

Hope this helps.

---

