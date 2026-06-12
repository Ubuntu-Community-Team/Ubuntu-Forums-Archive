---
title: "startup error"
date: 2009-09-19
forum: Desktop Environments
---

### Post by Ancient Dragon on 2009-09-19
When I boot up ubuntu I get an error box that says $HOME/.dmrc can not be accessed, and tells me it needs 644 permissions and me as owner.  I viewed the file permissions and had to change them to 644.  But when I reboot it gives me the same error message.

I also now have a problem starting FF 3.5 -- I don't know if it is a related problem or not.  I tried to install a plugin earlier this evening and it just kept displaying "installing ..." and never did finish.  It was after that that I started having these two problems.

I uninstalled FF 3.5, rebooted and got the warning about .dmrc again, then reinstalled FF 3.5 via Synaptic.  rebooted and still can not run it.

Anyone know how to fix these two problems?

---

### Post by drs305 on 2009-09-19
Follow the instructions in this guide I wrote about .dmrc errors:
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")

Try starting firefox in a terminal ("firefox-3.5") and post the error message (after you have fixed the .dmrc problem).


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by Ancient Dragon on 2009-09-19
Thanks -- that seemed to fix both problems.

---

