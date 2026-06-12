---
title: "Disabling Middle Click Paste"
date: 2007-05-01
forum: Desktop Environments
---

### Post by syko21 on 2007-05-01
when i use ubuntu on my desktop the middle click paste shortcut is pretty damn useful i must say. My laptop is another story, the trackpad is in the middle (HP dv6000t) so while I'm typing my wrist occasionally grazes the pad and since there is a scroll on the side a light graze is the equivalent of a middle mouse click. This has the tendency to paste random links or snippets of text where they do not belong. Is there any way to disable this?

---

### Post by fallingleaf on 2007-05-09
I'm looking for how to do this as well.  From what I can tell it is built in to X and might be difficult to change.  I'm using a Thinkpad with a trackpoint.  I use the middle button and up and down with the trackpoint to scroll.  If I accidentally hit the middle button without scrolling, I end up pasting stuff into my php code in random spots.  I have a habit of selecting text in my browser while i'm reading it so I end up with strange things in there!  There seems to be a fanaticism about this middle-click pasting to the point that I don't know if anyone would tell us how to do it even if it's possible.

Funny thing is, I never had this problem when using Edgy with Gnome desktop.  I did a fresh install of Kubuntu Feisty  and now it is driving me nuts.  This, among other things, may lead me to switch back to Ubuntu.

---

### Post by happyhamster on 2007-05-10
You can try some options in xorg.conf, see: [http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html](http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html)


For example, if I would want to disable the middle-mouse button on my standard 3-buttoned mouse:

	sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

	sudo gedit /etc/X11/xorg.conf


The mouse section in my xorg.conf looks like:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"	
EndSection


If I insert the line:

	Option 		"ButtonMapping" 	"1 3 3" 


Save, and restart X (ctrl-alt-backspace). The middle mouse button now behaves like the right one does. Similarly:

	Option 		"ButtonMapping" 	"1 1 3" 

makes the middle button behave like the left one, and "1 2 3 4 9 6 7 8 9" would probably change the middle button for some futuristic 9-buttoned mouse. Note that I can still paste using the mouse in this case (by clicking the right and left buttons simultaneously (because of the "Emulate3Buttons"	"true" option)).

For laptops the solution may be a bit different, but as long as the driver in your xorg.conf is also "mouse", then probably not too different.

Hope this helps.

---

### Post by syko21 on 2007-05-10
ill try the options out, one of them is bound to do what we want....
i like that i can scroll with the edge of the trackpad i just don't want a tap on that area to equate to a middle mouse button click

---

### Post by fallingleaf on 2007-05-11
Thanks syko21,

A lot of useful stuff on that page.  Unfortunately, I don't actually want to disable the middle button.  I like using it to open links in a new tab on Firefox.  This is my xorg.conf mouse section:
[INDENT]
Section "InputDevice"
[INDENT]	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"EmulateWheel"	"true"
	Option		"EmulateWheelButton"	"2"
[/INDENT]EndSection
[/INDENT]

From what I've been reading, the middle-click paste may use a different buffer from the ctrl-c, ctrl-v paste.  Maybe the answer lies in disabling this buffer?

---

