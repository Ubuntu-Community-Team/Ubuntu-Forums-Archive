---
title: "Notify OSD shape"
date: 2010-11-21
forum: Desktop Environments
---

### Post by prangija on 2010-11-21
All of a sudden my notify OSD bubble has wrong shape; like the down and right part of it was cut off. I didn't change anything in the configuration or anything. Here's the screenshot:
[http://img228.imageshack.us/img228/5829/selection001q.png](http://img228.imageshack.us/img228/5829/selection001q.png)

---

### Post by sikander3786 on 2010-11-21
It would be better if you could produce a screenshot with a real OSD notification. You can hit Print Screen key, save the image, crop it and post it here.

---

### Post by prangija on 2010-11-21
The situation is the same. I did the test case because it's the same with "real" notification:
http://img225.imageshack.us/img225/6188/selection002.png

---

### Post by sikander3786 on 2010-11-21
> **prangija said:**
> The situation is the same. I did the test case because it's the same with "real" notification:
[http://img225.imageshack.us/img225/6188/selection002.png](http://img225.imageshack.us/img225/6188/selection002.png)
Try re-installing notify-osd by

```
sudo apt-get install --reinstall notify-osd
```

However I doubt if the problem is related to that...

You don't have problem with anyother graphics stuff on your computer?

Which version of Ubuntu is it? Graphics card? And are the proprietary drivers installed?

---

### Post by prangija on 2010-11-21
Reinstalled the package and still have the same problem. Proprietary Nvidia driver is installed.

---

### Post by sikander3786 on 2010-11-21
> **prangija said:**
> Reinstalled the package and still have the same problem. Proprietary Nvidia driver is installed.
I feel stumped at this one.

Please hang in there until some other mate jumps in.

---

### Post by prangija on 2010-11-21
;) Thanks for your replies...

---

### Post by prangija on 2010-11-22
The problem is in pixman; notify-osd isn't compatible with pixman > 0.18. Downgraded it from 0.20 to 0.18 and everything looks as intended again.

---

### Post by prince5 on 2011-01-04
guys,..
                         Because notify-osd incompatible with pixman 0.20:
[launchpad.net/notify-osd/+bug/670785]("https://bugs.launchpad.net/notify-osd/+bug/670785")
downgrade pixman to 0.18 will solve this problem.
                     
i hope its helps guys,..
thanks,..

---

