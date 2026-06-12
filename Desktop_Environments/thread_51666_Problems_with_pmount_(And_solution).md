---
title: "Problems with pmount (And solution)"
date: 2005-07-24
forum: Desktop Environments
---

### Post by exobuzz on 2005-07-24
Hi,

I noticed that once I had build a newer kernel than 2.6.10 partitions on my usb drive did not automount. I have also seen a variety of posts on the forum which may be connected to the same problem. 

Seems that libsysfs1 uses a function that was removed from newer kernels. A newer debian libsysfs1 seems to have solved the problem, so i build from the debian unstable source, and now my drives mount when i click on the icons... :)

here are some debs if anyone wants to try them. (For hoary)

Use at your own risk.

[http://totem.fix.no/~buzz/kubuntu/](http://totem.fix.no/~buzz/kubuntu/)

[edit] and i'm sure I've put this post in the wrong forum.. sorry...

---

### Post by damonw5 on 2005-07-25
Thanks, exobuzz. 

Could you post a bug at [http://bugzilla.ubuntu.com](http://bugzilla.ubuntu.com) which describes this in more detail? That way we can get it fixed sooner and without resorting to ugly hacks :)

---

### Post by exobuzz on 2005-07-26
I made an additional comment to the bug report

[http://bugzilla.ubuntu.com/show_bug.cgi?id=12961](http://bugzilla.ubuntu.com/show_bug.cgi?id=12961)

with a link to the debian bug which gave me the answers I was looking for.

here it is for your information

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=314985](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=314985)

---

