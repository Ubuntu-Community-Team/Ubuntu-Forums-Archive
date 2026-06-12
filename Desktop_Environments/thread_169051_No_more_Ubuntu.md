---
title: "No more Ubuntu?"
date: 2006-05-01
forum: Desktop Environments
---

### Post by Tipo on 2006-05-01
Hey guys,

Earlier today, I kept getting these warnings that firefox was acting up, and I've tried killing all the firefox processes, but it still kept giving me the same error, so I tried rebooting...

Now, it seems like GNOME won't load at all. I reboot, it goes through the normal process, I get to the log in screen, type my user name and password, and then I get a brown screen with a white mouse cursor... and that's it.

This is normally where the splash screen comes in, and I see GNOME loading, but no dice. By hitting Ctrl-Alt-F1, I am booted into the command line and can log in, but I wants my GNOME!:mad: 

Any ideas, or help, will be appreciated:)

---

### Post by Gannin on 2006-05-01
From the command line, try moving ~/.gnome to ~/.gnome~ and ~/.gnome2 to ~/.gnome2~ so the next time you start Gnome, you'll have fresh configuration files, but you'll have copies of your old configuration files on hand too.  That'll help determine if the problem is with something being messed up in the configuration, or if it's something else.

---

### Post by benbruscella on 2006-05-01
I think the fastest way would be to remove your home directory files (ie back it up and create a new one).  You will lose all you settings, but at least the desktop should work again.

---

### Post by Tipo on 2006-05-01
Thanks for the help guys, I was able to ssh all the important files out and do a clean install, everything seems to be working fine now.

---

