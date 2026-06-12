---
title: "smbfs problem in fstab"
date: 2005-04-10
forum: Desktop Environments
---

### Post by plockery on 2005-04-10
I have a home network where all the data is stored on a windows 2000 pc.

I can mount the data partition manually from the console with
# sudo mount -t smbfs //server/d /disks/G -o username=myusername,password=mypassword

But I do not seem to be able to get it to mount at boot with fstab.
The line that should work in fstab is
//server/d  /disks/G  smbfs  credentials=/root/credentials/.smbcredentials,dmask=777,fmask=777

I have created a /root/credentials/.smbcredentials file with my userrname and password in it.

When I reboot I get a message that says that the smb connection failed but the message goes buy too quick for me to have a look at it. I can't seem to find where it might be recorded either.

Does anyone know how to sort out this fstab problem?

---

### Post by edubarr on 2005-04-10
You can run 'dmesg' to see what happened during the boot and identify the exact error you have. I don't use samba, so I really don't know what could be wrong with your fstab, but I hope that this can give you more info on your problems.

---

### Post by plockery on 2005-04-10
I did run dmesg but can't see any reference to it.
dmesg doesn't seem to record everything that appears on the screen during bootup, but I always thought it was supposed to.
Does anyone know what dmesg records and doesn't record?

---

### Post by plockery on 2005-04-11
Some other thoughts:

1. Could it be that the network is not being brought up early enough for fstab to connect to the smb cross platform shares?

2. Is it a root user issue in fstab since I can sudo to it later? I ask this because I fiddled with Gentoo for a while (too long and too many roadblocks for me) and I had virtually the identical line in fstab which worked without a problem.

---

### Post by plockery on 2005-04-11
My problem now seems to be solved.
It appears that the problem was my .smbcredentails file.
While I had the appropriate format
username=xxxxx
password=xxxx
There was a blank line after that. Once I backspaced to the end of the password line and saved the file, fstab connected to the windows share.

---

### Post by airtonix on 2006-05-14
Is it safe to leave your password here in the root homefolder ?

---

