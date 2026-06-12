---
title: "nVidia Driver Help"
date: 2007-03-29
forum: Desktop Environments
---

### Post by CarlosinFL on 2007-03-29
I install Ubuntu 6.10 fine and then installed the latest nVidia drivers which worked great. I was getting great clarity but then one week later I had to reboot the machine and then it started back up in CLI mode only. I checked /etc/X11/xorg.conf file and everything looked fine. The driver was still set to "nvidia" but when I tried to stop and restart KDM, I would get nothing. 

I changed the driver to the generic "nv" and restarted KDM and it worked again. I had X-Windows working. 

I then tried this on my work PC and I had the same exact problem and I really don't know how to get the Nvidia drivers working again. Any thoughts or suggestions?

---

### Post by BartAfterDark on 2007-03-29
couldn't you try and reinstall the drivers (install the newest on top) ?

---

### Post by afilonov on 2007-03-29
Did you update kernel packages after installing Nvidia driver? In this case you need to reinstall Nvidia driver.

---

### Post by CarlosinFL on 2007-03-29
I have 2 kernels only on this machine as shown below:

```
root@tank:/home/cwilliams/Desktop# dpkg --show-kernels
**[COLOR="Red"]linux-image-2.6.17-10-generic                   install[/COLOR]**
linux-image-generic                                   install
```

The colored one seems to be active right now and the other was a generic installed via default. I will reinstall the Nvidia driver and see what happens!

Thanks!

---

### Post by CarlosinFL on 2007-03-29
OK - reinstalled and well - it worked. :)

Thanks for all your help!

[IMG]http://img259.imageshack.us/my.php?image=screenshotho6.png[/IMG]

---

