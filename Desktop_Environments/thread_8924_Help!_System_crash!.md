---
title: "Help! System crash!"
date: 2004-12-22
forum: Desktop Environments
---

### Post by erpe on 2004-12-22
We'll I managed to break my system  :-(  Last thing i did was installing the newest rhytmbox version off the unstable repository. After a reboort  i got the following message:

There appears to be an X-server running on display :0
Should i try another display now?

If you you answer no i will attempt to start the server on :0 again


 :confused: 

We'll both options lead to nothin i cant  get into my desktop  :cry: 
I hope someone can ecplain to me whats happening here?

TIA

---

### Post by taygan on 2004-12-22
Hmmm.. I had the same breakage installing firestarter from hoary..  My solution was a dist-upgrade to hoary.. Maybe if you can downgrade the packages you installed you can save the system, dunno.

It seems that mixing warty and hoary is more dangerous than a full upgrade to hoary..  I installed hoary clamAV-0.80 and a few other packages into warty without problems, but firestarter didn't agree with my warty system.  A safer bet would be to backport a package or two from ubuntu backports, but if we're gonna live cutting edge we gotta commit!!

backports page:

[http://ubuntu-bp.sourceforge.net/](http://ubuntu-bp.sourceforge.net/)

or, for you, update your /etc/apt/sources.list to look like this:

[http://www.ubuntulinux.org/wiki/GuideToHoary](http://www.ubuntulinux.org/wiki/GuideToHoary) 

then try

```
$sudo apt-get update
$sudo apt-get dist-upgrade
```

It's over 500MB of downloads, but you get to keep your files and settings!

---

### Post by erpe on 2004-12-22
ok! Thanks for the advice!

---

