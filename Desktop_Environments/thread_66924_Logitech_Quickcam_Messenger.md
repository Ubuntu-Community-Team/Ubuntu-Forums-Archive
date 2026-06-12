---
title: "Logitech Quickcam Messenger"
date: 2005-09-18
forum: Desktop Environments
---

### Post by Seb Spiers on 2005-09-18
Have followed the howto; but I just get "no device found" in gnomemeeting.  :/

---

### Post by mlomker on 2005-09-18
[QUOTE=Seb Spiers]Have followed the howto; but I just get "no device found" in gnomemeeting.  :/[/QUOTE]

Not sure what how-to that is, but I assume you've loaded a driver.  What does **dmesg | tail** tell you after loading the driver?  It should create a port, such as /dev/video0.

---

