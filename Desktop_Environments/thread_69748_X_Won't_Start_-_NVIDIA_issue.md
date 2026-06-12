---
title: "X Won't Start - NVIDIA issue?"
date: 2005-09-27
forum: Desktop Environments
---

### Post by katiad on 2005-09-27
Hi everyone. Have a problem.... Power went off, and when I rebooted the computer, I get an error when X tries to start. I'm on the windows box right now... not sure what all I need, but I checked the error log and I get:

XIO: fatal IO error 104

Failed to load NVIDIA kernel module
Screens found, but none have a usable configuration.

What can I do to resolve this?

---

### Post by strikeforce on 2005-09-27
Reinstall the nvidia driver.  Also make sure the nvidia driver is current by typing sudo modprobe nvidia

It should just move to the next line.

If you want to check that your nvidia module is installed have a look at the output of lsmod | grep nvidia

You'll be able to narrow it down from there as to what the issue is.  Although it seems to me that the nvidia driver can't be found.

---

### Post by katiad on 2005-09-27
Thanks! Reloaded nvidia driver... all is well again! :cool:

---

