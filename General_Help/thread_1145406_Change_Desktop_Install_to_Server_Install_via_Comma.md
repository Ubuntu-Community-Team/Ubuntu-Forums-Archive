---
title: "Change Desktop Install to Server Install via Command Line / Putty"
date: 2009-05-01
forum: General Help
---

### Post by ds0101 on 2009-05-01
All,

I know this is a weird request, but I installed Ubuntu on an old PC for ham radio usage when I was very new to Linux two years ago and I unknowingly installed 7.10 Desktop.  This machine is located several hours away from me.  I now would like to remove all the unneeded desktop software from this machine, leaving a minimal install.  I can access this machine via SSH with Putty.

Thanks in advance.

D. Smith

---

### Post by Brandon Williams on 2009-05-01
You should really only attempt this if you feel very confident that you can recognize the packages that your system cannot do without. If that isn't the case, then you should only try this when you are physically with the machine in question. If you feel confident, then continue on.

The easiest thing is to get rid of ubuntu-desktop and all packages that are part of ubuntu-desktop but not required by any other package. If you already have everything marked as auto-installed that can be, then all you need to do is use aptitude to remove ubuntu-desktop. If not, read on ...

Open aptitude: 'sudo aptitude'. Now, press '/' and search for ubuntu-desktop. When you find it, press Enter to get to the ubuntu-desktop info screen. Arrow down to highlight 'Depends' and press 'M'. This will ensure that all of the ubuntu-desktop packages are marked as auto-installed, which means aptitude will only keep them if they are required by other packages, too. Arrow down to 'Recommends' and press 'M' again. Press 'q', and with ubuntu-desktop still highlighted, press '-'. This will mark ubuntu-desktop and all packages that are only installed because they are part of ubuntu-desktop for removal. Press 'g', look over the resulting list to make sure that you aren't making a huge mistake, and then press 'g' again.

You now have a console/ssh-login-only system.

---

