---
title: "Xubuntu: turn off trackpad scrolling?"
date: 2007-04-26
forum: Desktop Environments
---

### Post by Slackpacker on 2007-04-26
I feel silly, but for the longest time I couldn't figure out why my pointer kept leaping across the screen...
The right side of my trackpad is set to scroll in Xubuntu Feisty - I don't think that was in Edgy/GNOME.  How do I turn it off?  It doesn't seem to be in the Settings...

---

### Post by stinkyj on 2007-04-27
this is driving me nuts too, probably the lowest point so far in my installation...

from the synaptics driver manpage:

*Vertical scrolling (button four and five events) through moving the finger on the right side of the touchpad.*

so maybe there's a ZAxisMapping 4 5 that should be commented out in /etc/X11/xorg.conf

now that i know what is causing this, i can avoid it (and maybe try and use it) :)

---

### Post by fwojciec on 2007-04-27
There is a program called "gsynaptics" (website [here]("http://gsynaptics.sourceforge.jp/")) that lets you set the touchpad properties (such as scrolling) using GUI.  Install via apt-get, it should appear in System/Preferences (in Gnome, not sure about XFCE but you should be able to find it in one of the menus, it'll be called Touchpad Settings or something like that).

In order for it to work you'll have to add 

        "SHMConfig"    "true"

To the device settings in xorg.conf (and restart x).

---

### Post by fwojciec on 2007-04-27
A good guide for configuring touchpad in Ubuntu (worked beautifully on my laptop):

[http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide]("http://www.debuntu.org/2006/06/18/67-how-to-setting-up-touchpad-on-a-laptop-a-complete-guide")

If you want to disable touchpad while typing look here:

[http://www.debuntu.org/2006/06/25/70-how-to-disabling-your-touchpad-while-typing]("http://www.debuntu.org/2006/06/25/70-how-to-disabling-your-touchpad-while-typing")

I hope that helps.

---

### Post by stinkyj on 2007-04-28
thanks for that tip, i installed gsynaptics and turned off the scrolling. it's a nice feature, but i'm so used to using the arrows for scrolling, and it drives me nuts on the terminal. sloppy fingers and a small trackpad, i guess...

---

### Post by tenbbs on 2007-12-02
> **stinkyj said:**
> thanks for that tip, i installed gsynaptics and turned off the scrolling. it's a nice feature, but i'm so used to using the arrows for scrolling, and it drives me nuts on the terminal. sloppy fingers and a small trackpad, i guess...

I'm running Xubuntu 7.10 and after installing gsynaptics, I can only find the gsynaptics tool by using AppFinder, it never populated into my Applications/Settings menu. Did any other XFCE users have this problem?

Can anyone tell me how to configure X / Xfce to start gsynaptics with my previous session settings? I'm lost...

-HelicopterJay

---

