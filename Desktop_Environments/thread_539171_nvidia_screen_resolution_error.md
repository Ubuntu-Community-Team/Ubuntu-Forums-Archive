---
title: "nvidia screen resolution error"
date: 2007-08-30
forum: Desktop Environments
---

### Post by Cerny on 2007-08-30
I was using the Nvidia GUI interface to change my screen resolution from 1024x768 to 1280x1024 and that worked all peachy. Then when I clicked to save my new resolution the screen to Save X Configuration popped up and I liked to save it under /etc/X11/xorg.conf and have it merge with existing file an error appear,

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.

This error appear whether or not I decide to have it merge with existing file.  The resolution stays yet when I reboot it's back to the last configured screen resolution. Just hoping anyone can shed some light on how to fix the error.

---

### Post by FuturePilot on 2007-08-30
You need to launch nvidia-settings as root so it can write the file. Try
```
gksudo nvidia-settings
```

---

### Post by Cerny on 2007-08-30
Sweet, thanks that solve my problem in a matter of seconds.

---

### Post by dodoland007 on 2007-09-10
Thanks
this works fine

---

