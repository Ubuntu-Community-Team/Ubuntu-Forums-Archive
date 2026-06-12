---
title: "Ubuntu does not boot without interaction"
date: 2008-12-09
forum: General Help
---

### Post by Skizz0tt on 2008-12-09
Ubuntu 8.10, at the bootsplash seems to pause until I press a key, any key.  If I hold it down, eventually it loads and everything is fine.  If I don't press a key, the startup process just sits there.

This post [http://ubuntuforums.org/showthread.php?p=6332315]("http://ubuntuforums.org/showthread.php?p=6332315") seems to have fixed it, but i'm not convinced it's related to the clocksource.  

The first time ubuntu hangs, I see the following:

Usb hub found
Hub 2-0:1.0:2 ports detected

.... most of what seems to follow has to do with USB.

Is there some log I can process to look into this deeper?

I'm running ubuntu on a Compaq presario f700

---

### Post by cmnorton on 2008-12-09
Is there any USB device plugged in that you could unplug and then try to reboot?

---

### Post by Skizz0tt on 2008-12-10
There are no USB devices plugged in.  Can I run a log to pinpoint the problems?

---

### Post by cmnorton on 2008-12-10
You can look at the output of dmesg and search through /var/log/kern.log, /var/log/syslog, and /var/log/messages.

---

### Post by Skizz0tt on 2008-12-11
Ok, i'll give that a shot.  Thanks.

---

