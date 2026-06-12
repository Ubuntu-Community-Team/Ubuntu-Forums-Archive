---
title: "Freezing after Login"
date: 2005-10-18
forum: Desktop Environments
---

### Post by eraos on 2005-10-18
After I type in my password and try to enter Gnome session, my screen freezes at the slash screen (?).  It gets to "Window Manager" and stops.  I can hit alt f1 to get into the console though.
I also can log in with FailSafe.

I did sudo dpkg-reconfigure gdm as well as dpkg-reconfigure xserver-xorg but it still hangs.

This happened after I downloaded and installed Automatix.. and i installed media codecs, java, firefox plugins and Timidity (midi for alsa)
I installed those, rebooted and that's when my first freeze occured,

also, once, when i hit alt f1, i saw a message saying "grep /etc/X11/default-display-manager no such file or directory.

Can anyone help or point me to a thread that will help?  I've looked through some.  
Could it relate to sound?

---

### Post by stoanhart on 2006-06-02
I just had this problem today. Go to your home directory, show hidden files, go into the .gnome2 folder, and delete the session file.

If that doesn't work, move your entire .gnome2 folder into some other folder (call it gnomebackup or something like that), then log out and log back in.

That should do it!

---

