---
title: "sluggish ubuntu"
date: 2005-05-07
forum: Desktop Environments
---

### Post by GOwin on 2005-05-07
peculiar message from log files:
 /var/log/messages
 /var/log/syslog

"May  8 11:46:00 kulaspiro kernel: Warning: CPU frequency is 500000, cpufreq assumed 650000 kHz."

Am I not running at full 650kHz? Could this be the reason my computer feels sluggish on linux compared to windows (I dual-boot on w2k)

---

### Post by BAshworth on 2005-05-08
Are you using a i386 kernel?  If so, have you tried using kernel more fine tuned for your processor?

---

### Post by GOwin on 2005-05-08
Yes, i believe so.

How do I fine tune it to my kernel then?

---

### Post by BAshworth on 2005-05-08
Well, that depends on what kind of processor you are using.

Type uname -a in a terminal, and look at what it says close to the end of the line that ends in GNU/Linux.

Check [http://ubuntuforums.org/showthread.php?t=28911](http://ubuntuforums.org/showthread.php?t=28911)  for more information.

---

