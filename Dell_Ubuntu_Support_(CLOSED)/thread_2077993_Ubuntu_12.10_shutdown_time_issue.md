---
title: "Ubuntu 12.10 shutdown time issue"
date: 2012-10-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bond17_007 on 2012-10-29
I had Ubuntu 12.04 on my Dell 1558 with the following Config:
i3
8GB RAM
128 GB SSD

it use to take less than 2 seconds to shutdown but since i update to 12.10, it takes about 5 second. I feel that there is something abnormal. 
I checked /var/log/syslog but cannot locate anything. While shutting down i see [Fail] next to Terminating all other processes but it flashes so quickly that i can not read it all. Since HDD is off by then, it doesnt get logged either. Any help would be appreciated.

---

### Post by thotz on 2012-10-30
I also experienced longer shutdown times on my Lenovo Thinkpad Edge. This might be not specific to your laptop.

---

### Post by mikewhatever on 2012-10-31
Shutting down in 5 seconds doesn't sound abnormal. I'd say it's normal and reasonable.

---

### Post by gbrainin on 2012-10-31
I'm at probably 12-15 seconds, using 12.04.  It used to be quicker, maybe 5-6 if I remember correctly.

---

### Post by sammiev on 2012-10-31
When they first released 12.10 I was shutting down in 3 seconds. After the updates less than a week later, I went from 3 seconds to 16 seconds. There is a bug report on this.

---

### Post by bond17_007 on 2012-11-04
Thanks guys.. Looks like its 12.10 issue.  But 2 sec shutdown with my ssd was phenomenal hopefully they release a patch soon.. If u know plz post the bug link to launchpad thanks.

---

### Post by mc4man on 2012-11-05
It's generally 4-500% longer in 12.10 vs. 12.04 on same hardware
(network manager seems to be involved, also on nouveau sometimes a few add. secs due to a 'gpu lockup' whatever

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1066484](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1066484)

Thread on during dev
[http://ubuntuforums.org/showthread.php?t=2070963](http://ubuntuforums.org/showthread.php?t=2070963)

---

