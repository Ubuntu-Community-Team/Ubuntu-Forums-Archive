---
title: "Problem launching Nautilus after upgrade to 12.10 and 13.04"
date: 2013-05-08
forum: Desktop Environments
---

### Post by iggi916 on 2013-05-08
So I was stupidly impatient and decided to upgrade to 12.10 and 13.04 from 12.04 for no reason, and after upgrading to 12.10 my nautilus doesn't work. When I try to launch it from the Launcher, the home folder appears then disappears. If I manage to click on any other folder in my home folder it's fine.

I was hoping upgrading to 13.04 would fix it, but no dice. Running nautilus in terminal gives the following error messages:

~> nautilus

(nautilus:6406): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(nautilus:6406): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed
Segmentation fault (core dumped)

Any help would be appreiated!

---

### Post by dino99 on 2013-05-08
only dist-upgrading continuously let the system with some borked settings left behind (thats why doing a fresh install is not wasting time)
you might need to clean the system:
- first check /etc/apt/sources.list to be sure you now use 13.04 archives, and not some oldish ones. 
- update if required
- then clean: clean/autoclean/autoremove/gtkorphan/bleachbit

- reconfiguring:
sudo apt-get -f install
sudo dpkg-reconfigure -phigh -a
( be patient, can take a while)

and reboot

---

### Post by iggi916 on 2013-05-08
Thanks a lot! It seems to have worked. ALthough I did get a bunch of compiz errors while running sudo dpkg-reconfigure -phigh -a

As to your point about fresh install, can you recommend any way to make it easier/faster to re install all of my installed programs and packages upon doing a fresh install? Thanks!

---

