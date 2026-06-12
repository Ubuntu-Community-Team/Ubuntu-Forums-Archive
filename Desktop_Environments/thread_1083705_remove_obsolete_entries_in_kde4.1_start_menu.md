---
title: "remove obsolete entries in kde4.1 start menu??"
date: 2009-03-01
forum: Desktop Environments
---

### Post by atomizer on 2009-03-01
Hi....

Recently I removed wine to do an new install with the package from wine themselves.

Now when I type "wine" in the searchbox, my KDE4.1 menu still shows all the wine entries (from old games I installed before like "uninstall simcity 4" and "play railroad tycoon" and more like that.)

How can I remove those obsolete links?

---

### Post by chrisrhode on 2009-07-30
> **atomizer said:**
> Hi....

Recently I removed wine to do an new install with the package from wine themselves.

Now when I type "wine" in the searchbox, my KDE4.1 menu still shows all the wine entries (from old games I installed before like "uninstall simcity 4" and "play railroad tycoon" and more like that.)

How can I remove those obsolete links?

I too had this same problem - I found [this other post (click me)]("http://ubuntuforums.org/showthread.php?t=32136") on the forums (not sure if you did either) which gives the location of where the KDE menu is stored.  You can either edit the XML file with a text editor (such as Kate) or you can load the KDE Menu Editor (/usr/bin/kmenuedit) from terminal window and make the necessary changes there.  I'd opt for the latter as it was a lot more user-friendly.  I also made a shortcut to the KDE Menu Editor and placed it under the "system" folder so it was easier to get to.

Best of luck to you. :)

---

### Post by smsmith on 2009-08-04
> **chrisrhode said:**
> or you can load the KDE Menu Editor (/usr/bin/kmenuedit) from terminal window
Or just right click the kicker menu icon and choose "Menu Editor".

---

