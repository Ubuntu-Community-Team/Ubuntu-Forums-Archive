---
title: "Issues with desktop background"
date: 2014-06-10
forum: Desktop Environments
---

### Post by Areku The O.F. on 2014-06-10
I'm using Xubuntu 14.04 on a small Acer netbook and I'm experiencing a weird behavior with the desktop background. I've configured the lid to do nothing on close and when I reopen the lid the desktop momentarily shows a different background (specifically "solitude.jpg" from the default Xubuntu backgrounds) before reverting to the background I've configured. So far it only happens when I close and reopen the lid and while it's not really a deal-breaker for me it's kind of annoying and I would like to know why it happens. Any help would be greatly appreciated.

---

### Post by Toz on 2014-06-15
> **Areku The O.F. said:**
> I've configured the lid to do nothing on close
What exactly did you do here? What changes did you make? 
> and when I reopen the lid the desktop momentarily shows a different background (specifically "solitude.jpg" from the default Xubuntu backgrounds) before reverting to the background I've configured. So far it only happens when I close and reopen the lid and while it's not really a deal-breaker for me it's kind of annoying and I would like to know why it happens. Any help would be greatly appreciated.
Which screensaver are you using? light-locker? xscreensaver? What does the following return:
```
ps -ef | grep screensaver
ps -ef|grep light-lock
```

And finally, can you post the contents of /etc/systemd/logind.conf?

---

