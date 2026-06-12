---
title: "Delete Protected Drive"
date: 2006-06-04
forum: Desktop Environments
---

### Post by Steve S. on 2006-06-04
This may be in the wrong place...my system is Ubuntu Hoary I believe...

Hello all,

This is probably posted somewhere else, I just can't figure out what it would be listed under.

Here is the issue: when I initially set up this hard-drive (hd1 for the sake of explanation) I wanted to add some data from another hard-drive (hd2).

The transfer of data went off great (I set hd2 as a secondary drive to hd1) and then I removed the other drive.  But, after all was said and done, I have this file that is permissions protected, with nothing in it, that I can't delete.  It says that the owner is root and I simply don't know how to log in as root for that file to delete it...my command line isn't as good as many Linux-ers.

So, if someone could tell me how to command line that file out of there, or via gui, it would be very appreciated.

---

### Post by thunderduck3141 on 2006-06-04
to log in as root go to the gdm and press Ctrl Alt F1
type root for login
ur pass
then startx

---

### Post by aysiu on 2006-06-04
Press Alt-F2.
This will give you a Run dialogue.

In that dialogue, type ```
gksudo nautilus
``` if you're using Gnome or ```
kdesu konqueror
``` if you're using KDE.

---

### Post by Steve S. on 2006-06-06
Thanks, aysiu, worked great.

I also found that if I used the disc manager and went in there via the gui, it let me check everything and change restrictions, I'm assuming because I had to enter the root password to get into disc manager.

Thanks again, all.  Simple problem solved.

---

