---
title: "GNOME + KDE on one machine: Logging out hangs"
date: 2006-06-15
forum: Desktop Environments
---

### Post by timetunnel on 2006-06-15
Hi,
I just installed kubuntu-desktop additionally to my already existing ubuntu GNOME setup. I set the login manager to GDM. Everything worked fine except for one thing: when I log out of my GNOME session, the screen goes black for a short time (as usual), but then it won't reach the GDM screen and stays black. I'm neither able to reach the other terminals, nor does CTRL-ALT-BACKSPACE do anything. I have to switch off the computer then. This doesn't happen all the time but very often.

Any ideas?
Thanks
Jens

---

### Post by ajgreeny on 2006-06-15
Just to test out the system, in a terminal enter
sudo dpkg-reconfigure gdm
and change for the time being to kdm.

Now when you restart you will hopefully find that the problem has gone away.

You can always change back to gdm in the same way later if you prefer, but it may be worth reinstalling gdm using apt-get or synaptic, in case anything is corrupt in your current version.

---

