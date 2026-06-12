---
title: "Update timer-applet?"
date: 2010-01-25
forum: Desktop Environments
---

### Post by Mander on 2010-01-25
I like the timer applet but I wanted to get the sound working.  Since the Jaunty repository is out of date, I thought this might be the problem. I tried uninstalling and then installing from the source ([http://timerapplet.sourceforge.net/](http://timerapplet.sourceforge.net/)) but now when I try to add it to the panel I get the message "The panel encountered a problem while loading "OAFIID:TimerApplet". Do you want to delete the applet from your configuration?"

I don't really know what to do next to try and get the current versio working.  Any tips?

---

### Post by Mander on 2010-06-10
I've just started thinking about this problem again.  Is it possible that the problem is that the applet is looking for things called just "gnome" (as in python-gnome and python-gnome-desktop), rather than "gnome2" (python-gnome2 and python-gnome2-desktop)?  I had a look at the list of dependencies on the website for this applet, which is no longer being maintained, and I have at least the minimum versions of all of them.  The only difference is that "gnome2" thing.

Is there a relatively straightforward way for the ignorant person, such as myself, to make an appropriate change to the source code and install it?  I don't really know where to start looking for this kind of information, though.

---

### Post by TheOneEyedMan on 2011-05-04
I have this problem in Ubuntu 11.04 (Natty Narwhal) in 64 bit version. Timer used to work (in 10.04) but doesn't now. I've logged in with Ubuntu Classic and tried to add it back but get the following error message:

The panel encountered a problem while loading "OAFIID:TimerApplet".
Do you want to delete the applet from your configuration?

Any ideas?

---

