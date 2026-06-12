---
title: "Problems after apt-get upgrade"
date: 2011-06-03
forum: Desktop Environments
---

### Post by mogeb on 2011-06-03
Hi,
so i made a
sudo apt-get update
sudo apt-get upgrade libgdbus-1-2
Which started a lot of updates to other packages. After restarting my machine, I couldn't even start a session as i got the following message:



The following error was encountered. You may need to update your configuration to solve this. 
(EE) NVIDIA: Failed to lead the  NVIDIA kernel module. 


Maybe I should reinstall some drivers? If yes, how can I do so?


Graphic card: nVidia Corporation G84 [GeForce 8600 GT] (rev a1)


Thank you

---

### Post by Zorael on 2011-06-03
I don't recognize the error, but sure, reinstall the drivers. You need an Internet connection for this, though.

```
$ sudo apt-get update
$ sudo apt-get purge nvidia-current   # get rid of stray configuratiaon files
$ sudo apt-get install nvidia-current nvidia-settings
```

---

### Post by mogeb on 2011-06-05
Thank you for your reply. But the thing is I can't access any session on my machine. I can only run kubuntu from the Live CD. So how can i install the drivers? 
Can I just copy/paste the /etc/ folder from the CD?

---

### Post by mogeb on 2011-06-06
anyone?

---

### Post by Zorael on 2011-06-06
Try booting into recovery mode and pick **fix X** (or something along those lines). It should restore your xorg.conf to use the quite unaccelerated vesa driver, from which point you should be able to set up a net connection and reinstall your proper drivers.

---

