---
title: "No Gnome Desktop After I log In"
date: 2008-07-19
forum: Desktop Environments
---

### Post by EmyrB on 2008-07-19
Hi Guys,

I have Hardy Heron 8.04.01 64bit installed with the advanced desktop effects running and AWN. Since Thursday, everytime I log into Gnome, My desktop background does not appear (screen is black), there are no icons on the desktop and I cannot right click on the desktop. Compiz and AWN all run fine, well that is not strictly true the clock/calendar applet is very large so I have disabled it. Thinking about it, this happened at around the same time.

Anyway, I disabled desktop effects and rebooted and still the same thing after I log in, no desktop background, no icons, unable to right click on the desktop.

Everything else works in fact. The menu at the top, even the cairo main menu in AWN.

Any ideas?

Cheers

---

### Post by Mister.Vash on 2008-07-19
I had that happen before, it was an issue with a file.  In your home folder try renaming the following two folders and then reboot, the system should recreate them for you automatically

.metacity
.gnome

I'm pretty sure it was an issue with one of those two folders, but if that doesn't work you might have to try it with the other hidden folders, like .cache etc.

---

