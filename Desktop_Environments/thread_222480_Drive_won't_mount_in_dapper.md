---
title: "Drive won't mount in dapper"
date: 2006-07-25
forum: Desktop Environments
---

### Post by DAaaMan64 on 2006-07-25
Hey all, I need assistance.  My Dapper's got it out for my usb external hdd, my other linux install has no problem with it.  But everytime I go to mount it, it won't mount.  It says device not found etc.

I reformated it several times, but with no luck.  It used to work fine, however if it helps, I now receive this message if I have the external hdd on at boot.  

"sdb: assuming drive write cache through"
"sdb: assuming drive write cache through"

Please help.  This is very irritating and would justify reinstalling dapper yet again.

---

### Post by philippe_carlo on 2006-07-25
What do you do to mount it?

---

### Post by DAaaMan64 on 2006-07-25
I can mount it from cli or a file manager with the same response:

Could not mount device.
The reported error was:
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

---

### Post by philippe_carlo on 2006-07-25
```
sudo mkdir /media/data
```

```
sudo gedit /etc/fstab
```
Add line
```
/dev/sdb1        /media/data     auto    rw,user,noauto  0       0
```

```
mount /media/data
```

Now open the new disk icon on the desktop.

---

### Post by DAaaMan64 on 2006-07-25
wow that was interesting... It worked.  What exactly did you do, and why did it work?  If you don't mind explaining to the student...  Thanks you so much for you help.

---

### Post by philippe_carlo on 2006-07-25
Partitions that are mounted in /media always get a corresponding icon on the desktop (at least in Ubuntu). The rest I think, is just a matter of making sure the correct device is listed in fstab. /etc/fstab is used for correctly mounting all partitions at the right location in the FS-tree. A very important file! Try reading 

'man fstab'

if you want to learn more.

---

