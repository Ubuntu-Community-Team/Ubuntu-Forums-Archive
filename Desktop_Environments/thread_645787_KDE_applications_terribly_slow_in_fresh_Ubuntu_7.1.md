---
title: "KDE applications terribly slow in fresh Ubuntu 7.10"
date: 2007-12-20
forum: Desktop Environments
---

### Post by Daniao on 2007-12-20
Dear all,

I recently upgraded my Ubuntu system to the 7.10 version with Gnome desktop. From then on the KDE apps, specifically Kile (frontend for LateX compiling) are running terribly slow.

Googling for the topic I found some threads of people complaining about the same problem. Specifically:
[http://ubuntuforums.org/showthread.php?t=582921](http://ubuntuforums.org/showthread.php?t=582921)

In this thread it is recommended to remove the "xserver-xgl" to solve the problem. I tried that and it did solve the problem, Kile was running fas and smooth like before the upgrade. The problem is that after removing "xserver-xgl" many other things stopped working like I could not change the appearance of my desktop, or visualize remote folders using samba through nautilus.

Is there any fix to the problem cleaner than removing xserver-sgl? What are the functions of xserver-xgl ?

Thanks

Daniel

---

### Post by Daniao on 2007-12-20
I just had to look a bit more, the answer was in this thread:

[http://ubuntuforums.org/showthread.php?t=558731](http://ubuntuforums.org/showthread.php?t=558731)

Simply creating a file in "~/.config/xserver-xgl/disable" and restarting the X disable XGL and kde apps work smoothly.

Regards

Daniel

---

### Post by ram4nd on 2008-05-22
Thank you, it worked for me.

---

