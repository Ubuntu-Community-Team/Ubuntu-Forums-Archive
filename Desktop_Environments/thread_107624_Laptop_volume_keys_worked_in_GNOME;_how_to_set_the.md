---
title: "Laptop volume keys worked in GNOME; how to set them up in KDE?"
date: 2005-12-23
forum: Desktop Environments
---

### Post by grendel_khan on 2005-12-23
I've recently acquired a Compaq nx9500 laptop, which has mutimedia keys on it. When I first installed Ubuntu, I was pleased to note that (in the GNOME desktop) the 'multimedia keys' across the top of the keyboard worked; when I adjusted the volume, a small borderless window with a speaker icon and a slider bar popped up; the sound could be muted or adjusted with these buttons. I was pleasantly surprised that the buttons Just Worked.

I then installed kubuntu-desktop, and now the buttons don't work; pressing them does nothing. I did a bit of searching and found [an article]("http://www.djlosch.com/tutorial_debian.php#pcm_volume_link") (see 'enable multimedia keys...'), which pointed me toward the use of **xev**. I can tell you that the volume keys are sending keycodes 174 and 176 to lower and raise the volume, respectively, and 160 to mute, which appears to be pretty standard.

Where I'm stuck is how KDE actually implements these buttons. The audio mixer (KMix) documentation says that one can use DCOP calls; is there a small shim application that will, say, run **dcop kmix Mixer0 increaseVolume 0** at the proper time? Is this the sort of thing that's normally done automatically, but for some unknown reason my install bungled it? Is implementing them myself the proper thing to do here?

---

### Post by daller on 2005-12-26
Follow this howto:

[https://wiki.ubuntu.com/MultimediaKeys](https://wiki.ubuntu.com/MultimediaKeys)

Lower and raise can then be assigned these values in xmodmap.conf:

keycode 174 = XF86AudioLowerVolume
keycode 175 =
keycode 176 = XF86AudioRaiseVolume

Then an OSD-volume thing should appear... (when the rest of the howto has been followed - and you've restarted...)

The autostart shortcut should be placed in /home/<USER>/.kde/Autostart

---

### Post by dresnu on 2005-12-26
An other solution might be this [http://lineak.sourceforge.net/](http://lineak.sourceforge.net/)

---

