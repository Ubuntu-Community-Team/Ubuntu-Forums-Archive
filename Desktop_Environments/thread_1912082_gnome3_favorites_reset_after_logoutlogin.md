---
title: "gnome3 favorites reset after logout/login"
date: 2012-01-20
forum: Desktop Environments
---

### Post by mannyf on 2012-01-20
Good day again.

I am running Ubuntu 11.10 64Bit with gnome 3.  When I login, I removed some icons from the favorites task bar (on the left) and add new ones.  When I logout and login, the deleted icons are back and the new ones are gone.  Exhaustedly searched google and other forums and everything is talking about how to add apps to the the favorites (Right click --> Add to Favorites).  

Any help would be greatly appreciated.

---

### Post by mannyf on 2012-01-20
Also any changes with 'tweak' also get reversed as soon as I logout/login or restart.  I removed unity as well.  Strange Icons now for nautilus etc.

---

### Post by mannyf on 2012-01-25
OK, I ended up installing the updates that essentially uninstalled 'gnome-shell' and broke all kinds of things.  I re-installed Ubuntu 11.10 64 and installed gnome-shell.  After all my data was restored and after using it for a couple of days, the laptop locked up.  I could not use the mouse and then the machine just froze.  I rebooted the computer and it came back up except this time, it was showing the same behavior.  The changes I made with the tweak app were gone and the 'favorites' were the default ones again.

WHAT I DID:

I rebooted the machine, instead of logging into the GUI I logged into the cli.  Deleted the /etc/X11/xorg.conf.  I rebooted and all is well again.  Not sure this is going to keep though.  Has anyone else seen this type of behavior?

---

