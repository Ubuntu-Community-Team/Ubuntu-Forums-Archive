---
title: "Window Borders screwed up..."
date: 2007-12-01
forum: Desktop Effects &amp; Customization
---

### Post by Mattaus on 2007-12-01
Hi all,

Well recently I was mucking around with compiz and for some unknown reason typed *compiz info* into the terminal. It did some weird **** then said unrecognized command.

Everything seemed fine until I looked at the borders on my windows. There this weird red crap and look shite to me. Even when I applied some Apple-ish desktop custom pack thing it wont change. Everything else changed fine but the borders will not change from this red color (buttons are the same, they wont change)

What can I do to fix this!? Screen shot is attached.

Any help would be greatly appreciated. cheers.

---

### Post by FuturePilot on 2007-12-02
Try ```
gtk-window-decorator --replace
```
You must have installed Emerald. In Gutsy if Emerald is installed, it will be used by default.

---

### Post by fjpos on 2007-12-02
Compiz worked very nicely for a good time (GUTSY 7.10)  but after a troublesome reboot due to  power failure I have lost a significant amount of windows functionality such as no MAXIMISE MINIMISE, CLOSE WINDOW etc buttons on the top right of any window as well as no SCROLL bars. Terminal's text cannot now be seen and I cannot RESIZE or DRAG windows. Everything else works OK. Now I might have been heavy handed when I tried to correct this when I was using the Advanced Desktop Effects Settings under the System menu but most of the inadvertent changes there I have corrected. This is the second time is has happened and I can't remember what I did to fix the first time if in fact it did not fix itself. I have tried enabling and disabling effects, using and not using emerald, disabling and enabling the graphics (nvidia) restricted driver but nothing helps. Any help would be appreciated.:confused:

Thank you

---

### Post by Mattaus on 2007-12-02
fjpos....im new to this (as in first time Linux user, been at it for about 2 weeks now) so I really have no idea. Hopefully some one who does will read your post and be able to help you.

futurepilot, typing that into console works great, the windows fix themselves fine....except for one thing. It obviously executes the command, but no new command line comes up. It's like its still thinking about it. Cause if I close the terminal at any point the title bars at the top of the windows disappear completely. If I open a new terminal and run it again they come back. Except its the same as before if I close the terminal they disappear!

wtf?

---

### Post by fjpos on 2007-12-02
Hi 
I almost gave up with my problem but found the help in Compiz's FAQ ([http://compiz.org/FAQ/Users#I_can.27t_get_dBus_to_load_properly._What_do_I_do.3F](http://compiz.org/FAQ/Users#I_can.27t_get_dBus_to_load_properly._What_do_I_do.3F))  i.e.

---------------------------------------------------------------------------------------------------------------------
 My window borders do not appear.

First you need to check to see if Compiz started properly. Try to move a window by pressing alt and then dragging the window, if it moves then Compiz is running. If it does not then you need to fix that problem first.

If that works then check the following things.

    * Check that the decoration plugin is loaded
    * Make sure the Device section of your xorg.conf file contains this line 'Option "AddARGBGLXVisuals" "True"' 

If you have checked those things, then go to a terminal and type gtk-window-decorator --replace. If your window borders do not appear then please post the output to the forum.
--------------------------------------------------------------------------------------------------------------------
Note I didn't "gtk-window-decorator --replace" as above I just restarted the X server (reboot if you want). This sort of makes sense now as the original problem required me to use a xconf backup (once again the importance of backuping up).which did not have "AddARGBGLXVisuals" "True"' . Although my backup xconf (found in /etc/X11) also had and extra "Add....." see part of my xconf

Section "Device"
	Identifier	"nVidia Corporation NV11 [GeForce2 MX/MX 400]"
	Boardname	"nv"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Screen	0
EndSection 

I hope this helps other people

bye:guitar:

---

### Post by FuturePilot on 2007-12-02
> **Mattaus said:**
> fjpos....im new to this (as in first time Linux user, been at it for about 2 weeks now) so I really have no idea. Hopefully some one who does will read your post and be able to help you.

futurepilot, typing that into console works great, the windows fix themselves fine....except for one thing. It obviously executes the command, but no new command line comes up. It's like its still thinking about it. Cause if I close the terminal at any point the title bars at the top of the windows disappear completely. If I open a new terminal and run it again they come back. Except its the same as before if I close the terminal they disappear!

wtf?

Try running it from Alt+F2

---

### Post by Mattaus on 2007-12-02
I installed a new window package thingy-ma-bob and restarted and it seems to be fine now. I'm learning fast that alot of things in Linux require a fresh boot....

---

