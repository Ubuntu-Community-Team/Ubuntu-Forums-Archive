---
title: "HOWTO: Saitek Gaming Mouse"
date: 2005-09-20
forum: Gaming &amp; Leisure
---

### Post by shawn on 2005-09-20
I ordered myself a nice Saitek Gaming Mouse from the Net a few days ago. It has 6 buttons including the scroll wheel. I was a little concerned that I wouldn't be able to get all the buttons and features I wanted under Ubuntu, needless to say I now have a 800/1600dpi switchable 6 button gaming mouse working perfectly.

This will work for many types of mouse as far as I can gather, although I can only report that the Saitek works perfectly with these settings. Also, to get the mouse running like this in WinXP I would have to use crappy TSR (do people still use that term?) macro software I believe.

This does all I need easily - 6 buttons, scrollwheel and forwards/backwards buttons in firefox.

Here is the procedure, its simple:

> sudo gedit /usr/etc/X11/xorg.conf

Now locate your mouse settings section, its easily spotted it has several references to the mouse, like this:

> 
Section "InputDevice"

              Identifier	"Configured Mouse"
              Driver		"mouse"
              Option	   "CorePointer"

EndSection


Now you simply replace that section with the following:

> 
Section "InputDevice"
 	   Identifier	"Configured Mouse"
 	   Driver		"mouse"
 	   Option	   "CorePointer"
	 Option	 "Device" 			 "/dev/input/mice"
	 Option	 "Protocol"			 "ExplorerPS/2"
	 Option	 "Buttons" 			 "8"
 	 Option	   "ZAxisMapping"	 "4 5"
 	EndSection


Save, reboot or restart X (ctrl+alt+backspace) and all is done. Enjoy!

I now consider this mouse to be essential by the way. :)

---

### Post by feenster on 2007-01-14
Hi,
Dragging this thread up from the past a bit, but I have a Saitek Gaming Mouse, and couldn't get the scroll wheel working. Now got it working thanks to your guide, but can't get the forwards/backwards buttons working in Ubuntu 6.10. 

Any updated tips for getting this working?

Matt

---

### Post by josno on 2007-02-24
I would also like any info on this - I'm trying to get the same mouse working with the side buttons. Anyone have any joy?

---

