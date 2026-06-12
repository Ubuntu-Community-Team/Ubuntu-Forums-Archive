---
title: "gdm xsession fails start"
date: 2007-10-09
forum: Desktop Environments
---

### Post by kawabago on 2007-10-09
Feisty installed.  Desktop locked up using GoogleEarth.  Had to cut power to stop machine.  On reboot gdm fails to start my xsession.  This lockup has happened several times and caused me to reinstall ubuntu each time.  If I can't find out what's wrong, I'm not installing ubuntu again.

---

### Post by Digitallysick on 2007-10-09
can you paste the exact error its giving you?

---

### Post by kawabago on 2007-10-15
I solved this one.  I enabled the medibuntu repository to get a couple of libraries and left it enabled.  Over time incorrect packages from medibuntu were updating the system files and breaking everything.  This time I disabled Medibuntu repository immediately after installing what I needed so this won't happen again.
Thanks!
Powell River, BC, Canada

---

