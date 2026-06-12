---
title: "System unresponsive after suspend."
date: 2006-08-31
forum: Desktop Environments
---

### Post by Bastanteroma on 2006-08-31
Every so often when I resume from suspend to ram I can move the mouse and open the menus and some programs (firefox, for instance), but I can't load others (such as the terminal), the launch feedback comes and goes but no dice, or I click on quit and the logout menu doesn't show up.  Then 10-30 minutes later all the programs I clicked on suddenly load.  This doesn't happen on the first resume after a reboot, but other than that I can detect no pattern.  In most cases no programs are open when I suspend.  I ran automatix after installing but the only potentially disruptive thing that I'm aware of installing was beagle.  My computer is a fairly new dell dimension e310 with integrated graphics which otherwise suspends and hibernates without trouble.  I haven't noticed this problem after resuming from a suspend to disk, but I don't do that often enough to really say it works.

Any ideas?

---

### Post by Bastanteroma on 2006-09-21
stopping beagle fixed the problem - hopefully a newer kernel and beagle in edgy will work better.  Anyone know whether this is worth bug reporting and to whom (ubuntu devs, beagle crew)?

EDIT: problem recurred without beagle, so much for my  guess.

---

### Post by LosD on 2006-09-23
I'm pretty sure that Beagle is not to blame...

I don't dispute that it's Beagle that triggers the fault, but an application is not supposed to be able to screw up a kernel/X responsibility.

I think the right recipient would be the Ubuntu kernel or X team.

---

