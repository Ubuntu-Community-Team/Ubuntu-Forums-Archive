---
title: "Problems with GNOME Login Screen"
date: 2005-10-23
forum: Desktop Environments
---

### Post by kupad on 2005-10-23
My Login Screen's text is much too small to read.  I've tried several things to change it.

First, the most obvious, I changed my screen resolution to 800x600.  However, this only changed my resolution after the login screen - the login screen's resolution remained much too small.

I then configured xorg to not allow resolutions higher than 800x600 (using "sudo dpkg-reconfigure xserver-xorg").  This changed the login screen's resolution, but the text still remains much too small.

I then configured the login theme I'm using (Human) by using a text editor and changing the font sizes in the xml file (/usr/share/gdm/themes/Human/Human.xml). I changed everything to font size 14.  Nothing seems to have changed.

Can anyone tell me what to do to make this login screen readable?

--Kupad

---

### Post by traherom on 2005-10-23
Sorry, can't help you, but I know that my text got *bigger* with the upgrade. (from Hoary to Breezy) Maybe I'll be able solve that with your answer. :)

---

### Post by mykey on 2005-10-23
**sudo nano /etc/X11/xorg.conf**

take out the resolutions you do not need in  in the screen section - that should change the resolution for gdm

---

### Post by kupad on 2005-10-27
Even a resolution as low 640x480 leaves the text too small to read - but only for that login screen!

---

### Post by mykey on 2005-10-27
you mean when you use a different theme the fonts are o.k.?

---

### Post by kupad on 2005-10-28
What I mean is this:  Even if I set up xorg.conf to a low resolution with a low refresh rate, and a low color depth, the login screen remains unreadable.  Once I get past the login screen everything works fine.

Also, everything stays unreadable if I can get into another WM as well (like IceWM).

I've looked around everywhere for this problem and can't find any solutions.

---

### Post by rplantz on 2005-10-28
Have you tried one of the other "Themed Greeters"?

At System->Administration->Login Screen Setup

I found that "Happy GNOME" uses much larger fonts.

Bob

---

