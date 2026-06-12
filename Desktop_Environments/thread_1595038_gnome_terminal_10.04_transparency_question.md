---
title: "gnome terminal 10.04 transparency question"
date: 2010-10-12
forum: Desktop Environments
---

### Post by bhold on 2010-10-12
I have a Dell and HP system, both running 10.04 gnome desktop with latest patches. On the Dell system, the gnome terminal background is solid. On the HP system it is transparent.

In the "Appearances" configuration both use the Dust theme, both specify no visual effects. With gconf-editor looking at the gnome-terminal Default profile, both systems have background_type solid.

Thats all I know how to check. Would appreciate some help on how to get rid
of the transparency on the HP system.

In case it matters - the Dell system was was installed from a 10.04 CD, the HP system from a 10.04.1 CD. But I am pretty sure these are identical as long as both systems are up to date on all patches.

---

### Post by lapgoat on 2010-10-13
All you have to do is in gnome-terminal go to Edit > Profile Preferences, then at the top of the window go to the Background tab.  You can make your changes in there and it will be universal for all terminals you load with that profile.

---

### Post by bhold on 2010-10-13
lapgoat - On the HP system I edited background preferences in gnome terminal - set it to "Solid color". It did not work. But on the Dell system it works correctly.

So instead on the HP system I set it to "Transparent background" and set the slider for maximum shade. That worked, the terminal background is now solid. Seems a strange way to go about it, but it worked.

FYI, see launchpad bug #549552, [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/549552](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/549552)

---

