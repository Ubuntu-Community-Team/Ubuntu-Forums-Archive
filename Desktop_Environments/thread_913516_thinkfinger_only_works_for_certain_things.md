---
title: "thinkfinger only works for certain things"
date: 2008-09-07
forum: Desktop Environments
---

### Post by anystupidname on 2008-09-07
Just got a T42 stinkpad and installed kubuntu 8.04 on it. I followed the instructions here [http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger) to get the fingerprint reader to work but it only works for su or sudo operations. If I ctrl-alt-f1 for example I can't use it to input the password there and I can't use it to login initially to KDE or unlock KDE if I've locked it... Do I need to do something for it to interface with KDM or what? Assistance would be much appreciated.

---

### Post by e04mk on 2008-09-19
Read the part about KDE in the link you posted.

---

### Post by anystupidname on 2008-09-27
Yea, I already saw that. Was hoping that somebody had already created a plugin or something...

---

### Post by chhamilton on 2008-10-03
You can replace KDM with GDM for the time being to allow you to login with a fingerprint.  As to unlocking the desktop, I wrote a little wrapper to kdesktop_lock that makes the fingerprint scanner work.  It's a bit of a hack, but it works until a proper fix comes out.  I talk about it in this post:

[http://ubuntuforums.org/showpost.php?p=5901136&postcount=5]("http://ubuntuforums.org/showpost.php?p=5901136&postcount=5")

Cheers,

Chris

---

