---
title: "Disabling autologin from command line"
date: 2013-11-16
forum: Desktop Environments
---

### Post by nick-workman on 2013-11-16
I have installed Lubuntu on my MSI Wind netbook with autologin enabled. I switched from the LXDE desktop environment to the LXDE QT option but this just gives me a black screen and I cannot do anything with it. If I reboot into recovery mode I can get to a root command line and I need to turn of autologin so that I can switch back to the standard LXDE desktop. I navigated to /etc/lxdm and then did **sudo nano default.conf**. I can comment out the line in this file which should disable the autologin but it won't allow me to save the changes to the file. It says the drive is read only. Is there a way I can get back to the login screen?.

---

### Post by steeldriver on 2013-11-16
To allow changes to be written from recovery mode, you need to remount the filesystem. You can either use the 'Root shell with networking' menu option (which remounts rw as a side effect) or issue a mount command from the root shell

```
# mount -o remount,rw /
```

Note that there is no space between the remount,rw options

---

### Post by nick-workman on 2013-11-16
Thanks steeldriver. That worked insofar as allowing me to edit the default.conf file and save the changes. Unfortunately, commenting out the line in this file has not re-enabled the login screen. Any other ideas?

---

### Post by nick-workman on 2013-11-16
Okay, I have figured it out. It was the lightdm.conf file I needed to edit. Thanks for the mount command that was useful.

---

### Post by steeldriver on 2013-11-16
OK that's good, yes it's not always obvious which dm each distro uses

---

