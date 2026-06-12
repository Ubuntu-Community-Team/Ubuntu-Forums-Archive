---
title: "back-up and restore compiz settings"
date: 2011-07-01
forum: Desktop Environments
---

### Post by RikoW on 2011-07-01
Dear all,

to back-up and eventually restore compiz settings, is it enough to back-up and restore the .compiz directory in $HOME?

Reason is that the setting in my classic gnome set-up are different and partially conflict with the unity settings. Since I want to be able to run both environment (to give Unity a chance) I'd like to be able to switch settings easily.

Thanks and cheers,

                 Riko

---

### Post by coffeecat on 2011-07-01
> **RikoW said:**
> to back-up and eventually restore compiz settings, is it enough to back-up and restore the .compiz directory in $HOME?

I've never tried this myself, but apparently it's even easier than that. You can do it from within compizconfig-settings-manager. Have a look here:

[http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html)

That page is for getting the desktop cube working in Unity, but it describes how to backup compiz settings near the beginning.

---

### Post by Duncan Williams on 2011-07-01
also `compiz fusion icon' is a good utility.
It works fine in ubuntu 11.04 / peppermint on my system.

[http://wiki.compiz.org/CompizFusionIcon](http://wiki.compiz.org/CompizFusionIcon)

---

### Post by RikoW on 2011-07-01
Thanks for the tips. That seems to work in principle (so far only checked ccsm, even though my unity set-up is still bombed and I diid manage to reset it properly).

But I actually was looking for a way that would also work from a terminal and tty in case I don't get a running desktop anymore.

It seems like .compiz does not do the trick since there are plenty of setting in .gconf/apps as well ..

Cheers,
            Riko

---

### Post by mdacova on 2011-10-26
> **RikoW said:**
> Thanks for the tips. That seems to work in principle (so far only checked ccsm, even though my unity set-up is still bombed and I diid manage to reset it properly).

But I actually was looking for a way that would also work from a terminal and tty in case I don't get a running desktop anymore.

It seems like .compiz does not do the trick since there are plenty of setting in .gconf/apps as well ..

Cheers,
            Riko

your are a star, restoring .compiz-1 and .gconf worked for me

---

### Post by jsuhr on 2012-11-21
In LMDE (hopefully similar to Ubuntu, my apologies if not) I found the file "~/.config/compiz/compizconfig/Default.ini", which appears to hold the majority of my custom Compiz configurations. Incidentally, "~/.gconf/apps/compiz/plugins/" contains dirs "ring" and "switcher", both of which contain subdirs "allscreens/options/" each with it's own "%gconf.xml" file, one holding my custom keybinding for next window, the other holding my custom keybinding for previous window.
Hope this helps.

---

### Post by Toz on 2012-11-21
This thread is over a year old. Please create a new thread and reference this thread if required.
Closing.

---

