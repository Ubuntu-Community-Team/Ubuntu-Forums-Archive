---
title: "Thunderbird crashing"
date: 2006-08-02
forum: Desktop Environments
---

### Post by jamaas on 2006-08-02
Can anyone tell me why thunderbird would crash on startup?  When I run it from terminal I get the following error message?

I've already reinstalled it.

Thanks

Jim

mozilla-thunderbird
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 /usr/lib/mozilla-thunderbird/run-mo zilla.sh: line 131:  5836 Segmentation fault      "$prog" ${1+"$@"}

---

### Post by pablo13 on 2006-08-03
Hi, the only idea that comes to my mind is to erase your user profile. It could be in different places I think for example ~/.thunderbird or ~/mozilla-thunderbird. Actually, don't erase it !!!! , just move it to another name to give a try and if it doesn't work put it back again. In case that works that would mean your profile is somehow corrupted.

Hope it helps,
Pablo

---

### Post by aysiu on 2006-08-03
I have bad news for you, only a few instances of this error exist on a Google search, and none has a definitive solution:
[http://ubuntuforums.org/showthread.php?t=856](http://ubuntuforums.org/showthread.php?t=856)
[http://lists.debian.org/debian-amd64/2005/10/msg00990.html](http://lists.debian.org/debian-amd64/2005/10/msg00990.html)

---

### Post by golfbuf on 2006-08-03
Yes, it works fine here, so it must be something in your profile or your extensions or themes.  Do you have any extensions or themes installed?  If so, you may need to recreate your user profile without them to get running again.

---

