---
title: "How do I keep ubuntu from checking for stuff I don't have at start up?"
date: 2009-02-06
forum: General Help
---

### Post by princerameses on 2009-02-06
It takes about 5 mins for ubuntu to start, because it checks for things like blutooth and such.. It just goes down a list..
I think it started when I installed the 200-something updates when I first installed ubuntu.

---

### Post by mb_webguy on 2009-02-06
The 200-something updates were just that -- security updates and bug fixes for the operating system and software included with Ubuntu.  

If you're talking about those things checked for during boot, that's a completely different issue.  Some of those which you don't use can be disabled or removed entirely.

Go to System->Administration->Services, and uncheck the things you *know* you don't use, such as Bluetooth.  If you don't know *exactly* what a service does, *don't* uncheck it just because you don't recognize it!  Some of them are necessary system services.

---

### Post by glotz on 2009-02-06
Take a look at these old threads
[http://ubuntuforums.org/showthread.php?t=89491](http://ubuntuforums.org/showthread.php?t=89491)
[http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)

---

### Post by princerameses on 2009-02-06
That worked. I unchecked blutooth, and it started much faster. thanks.

---

