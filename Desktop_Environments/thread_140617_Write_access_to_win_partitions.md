---
title: "Write access to win partitions?"
date: 2006-03-06
forum: Desktop Environments
---

### Post by orazios on 2006-03-06
I have just installed Ubuntu-5.10 on my hda. I have also a hdd1 and a hdd5 partition with vfat and  have managed to get access to the root account (why on earth does the installer assume it´s not needed?) and edited /etc/fstab so my vfat partitions mount to /media/win_1 and win_2 respectively. My problem now is that not even root can change the root ownership so I can write to the win discs from my user account. By the way i cant even write to the floppy!
I have no problem with SuSe 10 or with Mandriva L E but I like a lot of things with Ubuntu and if anyone can teach me how to get a decent access to my discs I would be a lot happier.

---

### Post by bb002 on 2006-03-06
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat) explains howto mount fat partitions so everyone can read/write. But since you are having problems with writing to a floppy...first make sure the read-only switch is off on the floppy then post your /etc/fstab.

---

### Post by carlosqueso on 2006-03-06
your vfat lines in your /etc/fstab file need to look like this: ```
/dev/hdd1  /media/win_1 vfat umask=0000 0 0
/dev/hdd5  /media/win_2  vfat umask=0000 0 0
```  Once you've made them look like that, unmount them type ```
sudo mount -a
``` and they should work.

---

### Post by Randomskk on 2006-03-06
There's a good reason for not having root by default.
[http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

---

