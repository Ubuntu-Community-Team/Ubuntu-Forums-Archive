---
title: "Xbox controller's left joystick has an inverted Y axis."
date: 2005-12-09
forum: Gaming &amp; Leisure
---

### Post by Unrivaled on 2005-12-09
Hey guys,
Using the default xpad module, and the gamepad's left stick has an inverted Y axis.
This is extremely annoying. Does anyone know how to fix it? I've tried looking around for answers, but strangely wasn't able to find anything about it. Got alot of pages for linux on the xbox, and crap like that.
Thanks in advance.

---

### Post by bjweeks on 2005-12-09
What???

---

### Post by Unrivaled on 2005-12-10
I took an Xbox gamepad, chopped the cable, and attached a USB end on it, and plugged it in. Ubuntu already has the drivers for it installed, called xpad.
There are two joysticks on the xbox controller, the right one works fine, however the left one is set up kinda wrong. It acts as though you are pressing down if you press up and up if you are pressing down.
I'm assuming more people have had this problem, and I see patches for it for other distros. The only file I've been able to download is an xpad.c file, which doesn't do me much good as gcc won't compile it, and if it did, I wouldn't know what the heck to do with it; execute it or throw it in some directory.
Thanks in advance!

---

### Post by frost_ad on 2005-12-10
Hold your controller upside down. Other than that I have no idea.

---

### Post by arcanistherogue on 2005-12-17
I would also like to know this.  I read this topic about a week ago, and when I was modding my controller today I thought to myself "Well, I sure hope I don't get that problem he was talking about." I do get it, and it REALLY is that annoying.

See, since I use KDE, in system settings you can configure joystick.  You can move the left thumbstick around and it will show you where it is on a scatter plot via X and Y coordinates, and I noticed the Y was inverted.  I calibrated, and that got it working great, but still inverted  Y.

On games like StepMania and ZSNES, this really doesnt matter, as when you hit up to bind the control to up it says that it binds it to joydown (which acts as up), just as unrivaled said.

However, when playing things like Mupen 64 or ePSXe, where it binds it to the Axis, not the button (pressure sensitive, DDR and super nintendo dont need that) it is inverted, even if you enter the controls in reverse.  

Bumping this up, really, if ANYONE has help on this it will be appreciated.  If worse comes to worst, I'll try to get my hands dirty and apply my small C/C++ knowledge to a patch, but I doubt it will be easy for me to make and I will make it soon.

EDIT: I said both X and Y were inverted after calibrating, my bad.

---

### Post by arcanistherogue on 2005-12-17
I think I found the solution.

It only works in KDE as far as I have tested, but I just assume that because you need KDE to configure it.

IF you have KDE 3.5.0, go to Kmenu > System Settings, then hit Joystick.  Hit calibrate, and when it asks you to put the Y axis to the minimum position, but it to the maximum, and when it asks for maximum put it to the minimum.  This inverts the controls, so they are doubly inverted, which makes them work normally.

---

### Post by MetalMusicAddict on 2005-12-17
Wow. This is pretty cool. Im gonna try this in Ubuntu. :)

---

### Post by arcanistherogue on 2005-12-18
Yeah, its nifty.  And real easy too.  You can make it so it still works with the Xbox (thats what I originally tried) but im not too good with soldering and I messed it up, so I just stripped like 2 inches off both ends then soldered the usb and the xbox cables together at the right colors, then insulated them with electric tape, then wrapped them all together with electric tape

---

### Post by dude2425 on 2005-12-18
I've also had a few problems with this. Try jscal, or jscalibrate. It might help a little bit.

---

### Post by north on 2005-12-20
[QUOTE=dude2425]I've also had a few problems with this. Try jscal, or jscalibrate. It might help a little bit.[/QUOTE]

jscal works.  If you use jscalibrator you won't be able to use the D-pad.  Doesn't really matter though.  Forget about calibrating it with the inverted axis.  I'm assuming you guys are using joymouse to translate stick movement into mouse for those games that don't support joystick right?  Try this program.  It maps joystick data to keystrokes or mouse movement.  It'll swap the axis for you as one of the options.  Anyway it's called qjoypad, here you go:

Note: this doesn't set up your joystick.  It's not a driver or anything like that.  You still need to run jscal to configure your xpad.  It just lets you move buttons around and such. It won't make much difference in games that use the joystick natively...unless you choose not to use the joystick in the game and map the controller to mouse an key commands and use them.

 [http://prdownloads.sourceforge.net/q...3.4-1_i386.deb](http://prdownloads.sourceforge.net/q...3.4-1_i386.deb)
**sudo dkpg -i /wherever/qjoypad_3.4-1_i386.deb**

chances are you'll get an install error something like:

Unpacking qjoypad (from qjoypad_3.4-1_i386.deb) ...
[I]dpkg: dependency problems prevent configuration of qjoypad:
qjoypad depends on libqt3c102-mt; however:
Package libqt3c102-mt is not installed.[/I]if so do this and try again:

**sudo apt-get install libqt3c102-mt**

when you run the program you'll probably get an authentication error. Ignore it, even if it doesn't look like it's doing anything it's still running. Check the upper right hand corner of the taskbar next to the sound icon for a new blank space. double click and set up your joystick. If it's not there it probably opened up a small window somewhere on the screen.

---

### Post by north on 2005-12-20
[QUOTE=arcanistherogue]Yeah, its nifty.  And real easy too.  You can make it so it still works with the Xbox (thats what I originally tried) but im not too good with soldering and I messed it up, so I just stripped like 2 inches off both ends then soldered the usb and the xbox cables together at the right colors, then insulated them with electric tape, then wrapped them all together with electric tape[/QUOTE]

No need for soldering at all.  And buy a $5.00 controller extension, cut the end of that and tape same colours to same colours with a cut usb cord.  That way you just unplug your controller and plug it into the xbox.

---

### Post by &#12465;&#12452;&#12488; on 2006-08-04
My analogue left stick was inverted, and I tried to compile a newer xpad driver, but it didn't do any good. However, I tried calibrating the controller with jscal, and now it works great! Hurray!

The triggers are still detected as axises, though.

---

