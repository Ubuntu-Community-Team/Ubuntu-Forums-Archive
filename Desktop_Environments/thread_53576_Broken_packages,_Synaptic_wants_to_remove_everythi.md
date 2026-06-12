---
title: "Broken packages, Synaptic wants to remove everything"
date: 2005-08-01
forum: Desktop Environments
---

### Post by EndersGame on 2005-08-01
I had tried to install some additional packages using dpkg, but there were dependency problems and now they've showed up as broken in synaptic.  I want to simply remove them, but when I try to, Synaptic puts lots of other, important packages (like ubuntu-base and gcc) in the 'To be removed' list.  How can I clear these broken packages out of the system without removing all these other items?

---

### Post by adwait on 2005-08-01
dpkg -r <packagename> --force-all

Can potentially break your system...........

---

### Post by trashbird1240 on 2006-09-26
I have the same problem.  I tried to install tex-live from ftp.us.debian.org and i had a dependency problem.  I can install another tex package anyway, so no biggie.  Now, "fix broken packages" from the edit menu does nothing and...

When I try to install gcc from the Ubuntu CD and I hit apply, a dialog box comes up saying "To be installed..." gcc and company, "To be removed..." EVERYTHING! including all the libraries all the very recognizable packages like open office, abiword, and everything else, no joke.

I really need gcc, so I'd like to do it without wasting the system.

Thanks,
Joel

---

