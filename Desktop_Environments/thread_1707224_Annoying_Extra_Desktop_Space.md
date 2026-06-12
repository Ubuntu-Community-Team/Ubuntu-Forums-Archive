---
title: "Annoying Extra Desktop Space"
date: 2011-03-15
forum: Desktop Environments
---

### Post by tsarprodigy on 2011-03-15
Well... I have this stupid, annoying issue. it seems like there is some extra desktop space that i can't use... The pictures will show you what i'm talking about. On the laptop monitor, i can't see the empty right portion of the screen. For example,  when i took the Software Centre screenshot, it was maximized, and it filled the screen.

I'd be happy to answer any questions that might help lead to solving this issue. Any help is greatly appreciated!

---

### Post by randallecook on 2011-03-15
Weird. Could it be that there is a mismatch between the size of the desktop that the desktop manager (or is it a window manager?) thinks is available and what the X server (and underlying hardware) support? If this were true, then a maximized window would not fill the entire screen.

If you move a non-maximized window toward the right, so it extends beyond the right edge of a maximized window, does it appear to span two virtual desktops as displayed in the top taskbar?

I would fiddle with the display settings and try changing screen resolutions, and look at your X settings, too. Best of luck to you.

---

### Post by tsarprodigy on 2011-03-15
> **randallecook said:**
> Weird. Could it be that there is a mismatch between the size of the desktop that the desktop manager (or is it a window manager?) thinks is available and what the X server (and underlying hardware) support? If this were true, then a maximized window would not fill the entire screen.

If you move a non-maximized window toward the right, so it extends beyond the right edge of a maximized window, does it appear to span two virtual desktops as displayed in the top taskbar?

I would fiddle with the display settings and try changing screen resolutions, and look at your X settings, too. Best of luck to you.

Thanks for the reply. When I move a window to the right, it does not appear in another work space, however it appears in the  workspace switcher in that extra space. I've tried changing my resolution, and nothing really seems to be working... But i have noticed, if I restart the laptop, the problem is gone, for about 15 minutes, and it comes back out of nowhere...

and what do you mean by X Server and X settings? 

Also, when i move my mouse off screen to the right, it acts as if there is more desktop space there, and the mouse will keep going until the edge. I know that because I've lost my mouse too many times to count. 

I tried changing my resolution, though, and it was still set at my native resolution of 1280x800... I set the resize window info in Compiz so it would show the size of the window in pixels (#x#), and i noticed if i stretch a window over to the extra space, Compiz does NOT count it, yet the window still  resizes.

---

### Post by randallecook on 2011-03-15
The underlying graphical system on Linux is something called X Windows. The X server is a program that controls the display. X clients are regular apps like gedit that send graphics commands to the X server which displays them. The X server (XOrg these days on Ubuntu), its settings file, the window manager (a program that controls the look and feel of windows), the desktop manager (a program that controls the overall desktop--the graphical "shell" of your system), or some interplay among them is likely at fault. I recommend studying up on them and examining files to look for something wrong. Admittedly, this is difficult, but may be necessary.

The fact that it happens after 15 minutes is odd. Is there something in the system logs that could indicate a problem?

An experiment you could try is to boot your system from a liveCD and run it for 20-30 minutes to see if the problem occurs or not. If it does not, try to discover the difference between the liveCD configuration and yours.

Good luck. Graphics problems (and hardware incompatibilities) are Linux's Achilles Heels, IMO.

---

### Post by tsarprodigy on 2011-03-15
> **randallecook said:**
> The underlying graphical system on Linux is something called X Windows. The X server is a program that controls the display. X clients are regular apps like gedit that send graphics commands to the X server which displays them. The X server (XOrg these days on Ubuntu), its settings file, the window manager (a program that controls the look and feel of windows), the desktop manager (a program that controls the overall desktop--the graphical "shell" of your system), or some interplay among them is likely at fault. I recommend studying up on them and examining files to look for something wrong. Admittedly, this is difficult, but may be necessary.

The fact that it happens after 15 minutes is odd. Is there something in the system logs that could indicate a problem?

An experiment you could try is to boot your system from a liveCD and run it for 20-30 minutes to see if the problem occurs or not. If it does not, try to discover the difference between the liveCD configuration and yours.

Good luck. Graphics problems (and hardware incompatibilities) are Linux's Achilles Heels, IMO.


Thanks, i'll play with it and see what i can get... Although, i rebooted again, and it seems to be normal again. Its not doing it again, but i'll see if i can open any programs or change settings that might trigger the issue. I'll post more when/if i get something. I'll be sure to give details.

Thanks again!

---

