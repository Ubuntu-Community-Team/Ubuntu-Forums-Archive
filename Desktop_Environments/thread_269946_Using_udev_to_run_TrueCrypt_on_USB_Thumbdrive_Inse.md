---
title: "Using udev to run TrueCrypt on USB Thumbdrive Insertion"
date: 2006-10-02
forum: Desktop Environments
---

### Post by TiredBird on 2006-10-02
I have a thumbdrive with part of its contents encrypted by TrueCrypt. When I insert the thumbdrive into a USB port I want TrueCrypt to run and make the encrypted data immediately accessible but I can't get udev to execute TrueCrypt. I suspect that it has to do with privileges needed by TrueCrypt which udev won't grant, but I'm not sure. Hopefully someone reading this can help me solve my problem.

I am using udev rules. My /etc/udev/rules.d/10-local.rules file contains the following:

```
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", SYMLINK+="usb/*ThumbDrive*"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", RUN+="/home/*UserName*/bin/*Script-1*"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", RUN+="/home/*UserName*/bin/*Script-2*"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", RUN+="/home/*UserName*/bin/*Script-3*"
ENV{ACTION}=="add", KERNEL=="sd?1", SYSFS{serial}=="075410940A84", OPTIONS+="last_rule"
```

/home/*UserName*/bin/*Script-1*:
```
#! /bin/bash
/bin/mount /dev/usb/*Thumbdrive*
```
/home/*UserName*/bin/*Script-2*:
```
#! /bin/bash
/usr/bin/truecrypt -N 1 -p '' -k /home/*UserName*/*ThumbDrive*/TrueCrypt/*KeyDirectory* /home/*UserName*/*Thumbdrive*/*TrueCryptDirectory*/*EncryptedContainer*
```
/home/*UserName*/bin/*Script-3*:
```
#! /bin/bash
/bin/mount /dev/mapper/truecrypt1
```
A line from /etc/fstab:
```
/dev/mapper/truecrypt1 /home/*UserName*/KRYPTO vfat user,rw,suid,dev,exec,auto,utf8,umask=000,uid=1000,gid=1000 0 0
```

The 'user:group' on TrueCrypt and all three script files is 'root:root'. TrueCrypt and the three scripts all have 'suid' set. TrueCrypt and the three scripts all have read/write/execute permission for the owner and read/write for group and others.

The scripts each function properly when executed from the command line, (sudo not necessary), but when executed by the RUN statements in udev the first script works but the second doesn't. 

(I realize that these should all be in one script but I currently have them in three separate scripts to make it easier to isolate the problem.)

**Can someone help please.** (I'm rather new at Linux so it won't surprise or offend me to find out I've done something really stupid.)

---

### Post by orb9220 on 2006-10-02
Also check out [http://forums.truecrypt.org/](http://forums.truecrypt.org/)

Sorry couldn't be more help.

---

### Post by TiredBird on 2006-10-03
I posted something similar on the TrueCrypt forum but I haven't gotten an answer yet. Also, I searched that entire forum and could find no mention of udev.

---

### Post by TiredBird on 2006-10-04
This problem got fixed thanks to some help in another thread. Here is the post that solved it for me: [http://www.ubuntuforums.org/showpost.php?p=1578267&postcount=22](http://www.ubuntuforums.org/showpost.php?p=1578267&postcount=22)

---

