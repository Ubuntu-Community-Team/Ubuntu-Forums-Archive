---
title: "Ubuntu 12.04 64-bit, KDE 4.8.2 - KDE Power Management System - error on login"
date: 2012-05-27
forum: Desktop Environments
---

### Post by _-LC-_ on 2012-05-27
Hello, :-)

I get the following error window (showing up for a few seconds then disappearing):
KDE Power Management System
The Profile "AC" tried to activate DPMSControl, a non existent action. This is usually due to an installation problem or to a configuration problem.

Any idea how to fix this?

Ubuntu 12.04 64-bit (shows after upgrading from 11.04 -> 11.10 -> 12.04)
KDE 4.8.2

Thanks a lot for your help!
                                                     LC

---

### Post by _-LC-_ on 2012-05-27
Correction - this seems to be only the case when running in a VM (VMware)...

---

### Post by mparillo on 2012-08-21
> **_-LC-_ said:**
> Correction - this seems to be only the case when running in a VM (VMware)...
It started happenning to me a day or so ago, running Kubuntu 12.10, in VMWare Player.
My [thread]("http://ubuntuforums.org/showthread.php?t=2045431").

One question: How were you able to capture the error message?

---

### Post by mparillo on 2012-08-22
> **_-LC-_ said:**
> Correction - this seems to be only the case when running in a VM (VMware)...

This could be an upstream product, as I found a similar bug on OpenSuSE:
[https://bugzilla.novell.com/show_bug.cgi?id=765679](https://bugzilla.novell.com/show_bug.cgi?id=765679)

---

### Post by mparillo on 2012-09-13
The warning stopped now that I have been updated to Platform Version 4.9.1.

---

