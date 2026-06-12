---
title: "My session crashes very often"
date: 2012-01-06
forum: Desktop Environments
---

### Post by Elvin85 on 2012-01-06
Hello. 
I use Ubuntu 11.10 with default Unity interface. Last 15-20 days i often meet such problem: During working my session suddenly crashes and system logges out. I log in again then after 1-2 hours it happens again. After each crash i log in and open /var/log/syslog file and see same error in crash time:

Jan  6 21:35:41 elvin-Aspire-5741 gnome-session[24121]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012

So i think this error can say a lot about my problem. Is there any idea? My laptop RAM is 4GB, core is i5. So hardware is not bad.

---

### Post by mquasar on 2012-04-17
I'm having the same crash on a Dell Vostro, running Ubuntu 11.10.

Have searched around and haven't found much info on the problem. Could be related to graphics cards drivers apparently.

Any ideas?

---

### Post by 2F4U on 2012-04-17
There exists a bug report on such an issue for Ubuntu 12.04.
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/937347](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/937347)

In the report they say it is due to the proprietary ATI driver.

What graphics card do you guys have and what graphics drivers do you use?

---

