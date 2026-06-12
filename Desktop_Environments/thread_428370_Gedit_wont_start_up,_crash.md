---
title: "Gedit wont start up, crash"
date: 2007-04-30
forum: Desktop Environments
---

### Post by hamil on 2007-04-30
Hello!

Not sure what has happened here, but I am no longer able to start Gedit...

I am on a AMD64 machine, with Ubuntu 64. I have not updated Gedit within the last days, either from synaptic nor any other places.. I have succesfully used Gedit with this installation earlier, but not for the last days....

The only changes I have made to my system, is installing Iceweasel32, flash, java, mplayerplug-in and some other 32 libraries, none that I can see how could affect Gedit.

When I did try to open my sources.list yesterday, nothing happened. The terminal just kept «working», and the Gnome-System-Monitor started to eat alot of my CPU. Nothing happened for almost three minutes, then the terminal stopped working with gedit, no errormessage was presented in the terminal, just another blank line...

I have also tried to start Gedit with the normal launcher from the menu, but then it only opens up a blank page, without any menues or anything. And I am not able to do anything but kill the gedit process.

From synaptic, I did try to reinstall Gedit today, but that did not help me at all. Everything stayed as it was before the reinstall.

I am really fond of Gedit, so any inputs to how I would be able to resolve this issue, would be appreciated!

Lasse

---

### Post by kodoku on 2007-04-30
did you try purging the configuration files?

In synaptic, "completely remove" gedit, and then clean reinstall

or

> sudo aptitude remove --purge gedit && sudo aptitude install gedit

---

### Post by hamil on 2007-04-30
Yes, I have tried to completely remove it, and reinstalling it afterwards, still the same reults. Nothing happens. Had a powerdown for an hour ago, and when the PC booted up again, gedit worked as an charm. Did a restart of X, and then it was no longer working again.

Tried to reinstall one more time, and issuing the sudo gedit /etc/apt... and it was hanging for some minutes, before the gedit window showed up for a millisecond, and then disapearing again. No error-message is visible in the terminal this time either.

---

### Post by hamil on 2007-04-30
Well, seems like there is more issues now...

Just so I have this stated, this is a freshly installed Feisty install (just a couple of days old). It has not been messed with, other than installing the necessary codecs etc with Automatix, and the installscript for Iceweasel.

Now I also have troubles with opening pictures. Seems like Nautilus eats alot of CPU, and is not able to open the pictures either. Just another white box showing up, not containing any pictures or menues.

I killed all instances of nautilus, and tried to open the picture agian, but this time in Gthumb, it opened it ok. And then by double klicking it in Nautilus, again it opened up ok. 

Something really strange is happening here...

---

