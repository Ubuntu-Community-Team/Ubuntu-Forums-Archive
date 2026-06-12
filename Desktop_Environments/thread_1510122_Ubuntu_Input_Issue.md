---
title: "Ubuntu Input Issue"
date: 2010-06-15
forum: Desktop Environments
---

### Post by eidanch on 2010-06-15
Dear supporters,

I had recently upgraded my 9.0.4 ubuntu to the latest version, but something must have gone horribly wrong during the upgrade. On boot, it says it has problems and errors loading stuff and when it gets to the desktop, it gets no input from the keyboard or the mouse. Same goes for recovery mode. When trying to run from a live CD the keyboard and mouse work just fine. I have the CD and I wanted to simply reinstall but problem is I don't know how to reinstall over the current installation.
If any one could help me it would be much appreciated.

Thank you,
E.C.

---

### Post by Paradoxfox93 on 2010-06-15
If your /home directory is a separate partition then you can use gparted in the LiveCD installation to declare that same partition as /home and do NOT select 'format'.  Your data and many settings (Browser bookmarks, history cookies, GNOME applets and launch icons etc.) will be retained.

If you did not do this on your original install you will have to back up your data.  This is an opportunity to do exactly this if you can spare a partition for it.

---

