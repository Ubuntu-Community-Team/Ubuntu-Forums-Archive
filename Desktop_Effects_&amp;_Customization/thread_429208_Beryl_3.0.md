---
title: "Beryl 3.0"
date: 2007-05-01
forum: Desktop Effects &amp; Customization
---

### Post by ZeroWing on 2007-05-01
Seems like a new update.

 That doesn't work for me. Just crashes back into metacity. Worked before... any way to fix this, or install a previous version?

---

### Post by nuttiplutt on 2007-05-01
There's a thread here with the same problem: [http://ubuntuforums.org/showthread.php?t=427946]("http://ubuntuforums.org/showthread.php?t=427946")

If you get to make it work, please post in that thread as well.

---

### Post by ZeroWing on 2007-05-01
No, it's not letting me downgrade, because Beryl did a bad hiccup during update. So, either the update didn't work, or the current version itself is damaged.

---

### Post by ZeroWing on 2007-05-01
> **ZeroWing said:**
> No, it's not letting me downgrade, because Beryl did a bad hiccup during update. So, either the update didn't work, or the current version itself is damaged.

 Bump. :(

---

### Post by rolf-c on 2007-05-01
Did you build 3.0 - I can't find it anywhere.  I see 0.2.0 and 0.2.1 but no 3.0.  Over at [http://www.beryl-project.org/releases.php](http://www.beryl-project.org/releases.php) they only list releases up to 0.2.1.

If you apt-get'd it, you can use the apt-get remove --purge option to whack it good then reinstall via apt-get.

---

### Post by Fireblend on 2007-05-01
Woah, where? I see no updates...

---

### Post by ZeroWing on 2007-05-01
What, are you kidding? I see it in Synaptic. Version 3.0+git20070324~3v1uuntu4.

---

### Post by evilc on 2007-05-01
> **ZeroWing said:**
> What, are you kidding? I see it in Synaptic. Version 3.0+git20070324~3v1uuntu4.

That refers to svn version which is "beta" type or some call bleeding edge,

---

### Post by ZeroWing on 2007-05-01
> **evilc said:**
> That refers to svn version which is "beta" type or some call bleeding edge,

 I don't believe that Ubuntu would allow me to update to a beta version by default.

 Oh, forget it. Beryl screwed my system. Had to reinstall.

 Sucks, too. I actually tried this time. :cry:

---

### Post by rolf-c on 2007-05-01
You may want to check your sources.list file at /etc/apt/sources.list for whatever repo is listing beryl 3.0.  I recommend you comment that (those) out and apt-get update to refresh your cache.

---

### Post by rsambuca on 2007-05-01
> **ZeroWing said:**
> What, are you kidding? I see it in Synaptic. Version 3.0+git20070324~3v1uuntu4.

Did you have Trevino's repository's in your sources list?

---

### Post by FuturePilot on 2007-05-01
This is usually to be expected from SVN.  Beryl 0.3.0 is a development release and therefore is going to be buggy.

---

