---
title: "How to modify Nvidia's X Server settings as 'root'."
date: 2011-09-11
forum: Desktop Environments
---

### Post by devcalais on 2011-09-11
Hey guys.

I'm trying to modify my X Server Display Configuration as I just installed a second (dual, now) monitor. 

I don't have a problem getting it set up how I like it, however it only lasts a single log-on, as I do not have 'root' access to save the settings to the Configuration File.

I don't think I ever created a 'root' user password, how do I get around this?

Cheers, TB.

---

### Post by papibe on 2011-09-11
Open a terminal, and run this:
```
$ gksudo nvidia-settings
```
gksudo is like sudo, but it will ask you your password graphically.
nvidia-settings is the actual program name of the Nvidia X Server Settings.

Hope it helps,
Regards.

---

### Post by devcalais on 2011-09-11
Excellent, something to remember. Thanks for the quick reply.

---

