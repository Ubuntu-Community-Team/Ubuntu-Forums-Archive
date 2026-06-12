---
title: "Mounting a drive at logon"
date: 2010-10-15
forum: Desktop Environments
---

### Post by Charlotte18 on 2010-10-15
I'm trying to have an internal drive mount at logon.  The drive is /dev/sdc, so I added this to the rc.local file:
```
mount /dev/sdc1 /media/disk
```
The problem is that the drive is not mounting. This is happening in 10.10.

---

### Post by Charlotte18 on 2010-10-15
Well, I feel stupid. I forgot to create the "disk" directory in /media.

---

### Post by annoyingrob on 2010-10-15
The correct way to do it is to put it in /etc/fstab
:)

---

### Post by Isyaltut on 2010-10-16
Also you can use pysdm if you'd like to edit /etc/fstab with gui.

I've come across this great tutorial at [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197) on how to setup mounting partition at login.

---

### Post by annoyingrob on 2010-10-16
I feel stupid, I read "Logon" as "Startup". I guess putting it in fstab just mounts it when you start the machine. Sorry.

---

