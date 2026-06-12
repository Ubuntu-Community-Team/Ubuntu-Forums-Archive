---
title: "Automatically setting drive permissions on startup"
date: 2005-12-10
forum: Desktop Environments
---

### Post by timelord726 on 2005-12-10
I'm running VMware Workstation on my computer, and one of the drives I have set to mount automatically is an external USB drive located at /dev/sdc.  Every time I restart my computer, VMware is unable to power on the virtual machine (insufficient permissions to access /dev/sdc) until I have run the following commands:

```
sudo chown danny /dev/sdc
sudo chmod 600 /dev/sdc
```

Is there something I can do to set these permissions accordingly once and for all so that I don't have to rerun these commands each time I restart?

Thanks!

---

### Post by amohanty on 2005-12-11
I think you can use the umask directive in fstab to set up permissions. See here:
[http://linux.about.com/od/linux101/l/blnewbie4_2_6.htm](http://linux.about.com/od/linux101/l/blnewbie4_2_6.htm)

eg in my box :

> /dev/sda1       /windows        ntfs    ro,user,auto,umask=022        0       0


umask specifies the mask for the permissions so a umask=000 sets the perms for a folder to be 777.

HTH

---

### Post by timelord726 on 2005-12-11
Thank you for the post, and the link.  What would be the correct umask value for a chmod of 600, and is there another command to give ownership to my user?

---

