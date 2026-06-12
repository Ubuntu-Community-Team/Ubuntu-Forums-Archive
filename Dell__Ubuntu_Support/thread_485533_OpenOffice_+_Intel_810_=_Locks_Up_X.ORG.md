---
title: "OpenOffice + Intel 810 = Locks Up X.ORG??"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by jazzcat on 2007-06-27
Howdy All,

We've run into a peculiar problem on the E1505N that came pre-loaded with Ubuntu Feisty Fawn.  Sometimes, when my fiancee is using it and she opens an OpenOffice menu item (to save the file for example), X.ORG completely freezes up.  The only way to rectify the situation is to either SSH into the box and kill openoffice, or press CTRL+ALT+F1 and then a combination of the Fn key and each one of the blue-labelled keys.  That usually shakes it to the point we can get to a login prompt on tty1 and kill openoffice.  After openoffice is dead, things return to normal.

I believe this is a problem with XORG and Intel-8XX based video drivers.  I have a Shuttle PC running CentOS 5 with a lower-numbered Intel 835 (I think) and we had the same issue.

Is anyone else seeing this, or have a resolution?

Later,
-J

---

### Post by whizbaby on 2007-06-27
Hmm, this sounds familiar to me (though you have different hardware)...
[http://ubuntuforums.org/showthread.php?t=475523&highlight=mess](http://ubuntuforums.org/showthread.php?t=475523&highlight=mess)

If you have feisty, try downloading the drivers from the intel homepage.
If you dont have feisty, get it!

---

### Post by syberdave on 2007-06-28
I have the same problem, but I have a nVidia Go 6150 card.

---

### Post by whizbaby on 2007-06-29
> **syberdave said:**
> I have the same problem, but I have a nVidia Go 6150 card.
For future posts try being more verbose, nobody knows what driver you are using so its hard to say anything.
So, what driver are you using (vesa, nvidia-glx, newest driver release from nvidia ) ???

---

### Post by syberdave on 2007-06-29
I'm using nVidia's drivers, version 1.0.9755
X.org 7.2.0
OpenOffice 2.2

---

### Post by whizbaby on 2007-06-29
What configuration options have you set in xorg.conf? Is composite enabled (e.g. makes my GForce2 hang when I open synaptic)?

---

### Post by syberdave on 2007-06-29
Here's all the stuff relevant to the graphics card:

> Section "Device"

#	BusID       "00:10:3"
    Identifier     "Card0"
    Driver         "nvidia"
    Option	"AddARGBGLXVisuals"
Option "AllowGLXWithComposite"
Option "TripleBuffer"
Option "AddARGBGLXVisuals"
Option "NoLogo"
Option "NvAGP" "1"

EndSection

Section "Extensions"
	Option	"Composite" "enable"
	
EndSection

I turned off OpenGL in OO.o and if that doesn't solve it, I guess I'll try turning off Composite. Unless you know it's composite for sure, of course.

---

### Post by whizbaby on 2007-06-29
Composite causes problems on some (not all) nvidia cards. It has to do with agpgart and nvagp (both kernel modules, the first one is loaded by default and nontrivial to remove). With nvagp it may work, but using agpgart I would try to uncomment (that is putting an # in front of the line)

AllowGLXwithComposite

and set composite to "disable"

Then restart the xserver (if you dont know howto hit ctrl-alt-backspace) and retry  o_O

---

