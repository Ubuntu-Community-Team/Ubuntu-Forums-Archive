---
title: "Xubuntu + Flash + No Sound."
date: 2005-12-06
forum: Desktop Environments
---

### Post by Joey French on 2005-12-06
Hi all,
I have recently begun using xfce and love it. I can load up amarok and play tunes, no problem. However, when I go to flash sites, (ie, Homestarrunner.com) I have no sound! How will I ever be able to use Xubuntu (which i heart to death), if I can not watch Strongbad's Email?!?

It's that level of seriousness. Please help me get some flash sound up in my Xubuntu.

Joey French

---

### Post by Joe_CoT on 2005-12-06
as far as sound in flash goes, it's most probably fixed the same way in xubuntu as in regular ubuntu. have you tried fixing it like they say in this post?
[http://ubuntuforums.org/showthread.php?t=75237](http://ubuntuforums.org/showthread.php?t=75237)
i'd recommend trying this one-liner before messing with the rest of the how-to, though:
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

---

### Post by Joey French on 2005-12-09
Thanks, I'll try that. Anyone else have a problem with flash sound in xubuntu?

---

