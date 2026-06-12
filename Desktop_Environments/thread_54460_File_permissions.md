---
title: "File permissions"
date: 2005-08-04
forum: Desktop Environments
---

### Post by synap on 2005-08-04
I didnt get a responce to this in the gaming section and I cant for the life of me figure out what I need to change.  

I was hoping someone might know if there is a way to change the permissions permanently on these files?
/dev/input/event*

After each reboot it reset back to 600 and the drivers for the nostromo game pad need these to be 666.

Ref [post](http://www.ubuntuforums.org/showthread.php?t=53558)

Thank you!!

---

### Post by Juergen on 2005-08-04
The devices are dynamically created at each boot via udev.

I don't know what exactly needs to be done, but the config-files are in /etc/udev.

Maybe you can get something out of this:
[http://gentoo-wiki.com/HOWTO_Griffin_PowerMate_with_UDEV_and_Kernel_2.6.x#UDEV](http://gentoo-wiki.com/HOWTO_Griffin_PowerMate_with_UDEV_and_Kernel_2.6.x#UDEV)
Not for nostromo and not for Ubuntu but a starting point for experiments...

---

### Post by mpedrummer on 2005-08-04
Could you set up a CRON job to run at boot to change the permissions?

---

### Post by Juergen on 2005-08-05
I looked at /etc/udev/permissions.d/udev.permissions

I suppose it should work by just changing the line 'input/*:root:root:0600' or maybe better creating a new one for input/event*

---

