---
title: "Mounting NTFS external hard drive in Sidux?"
date: 2008-05-01
forum: Debian
---

### Post by patrickaupperle on 2008-05-01
I just bought an external herd drive and formated it NTFS. It works perfect in ubuntu (with ntfsprogs) and in windows. I popped in my Sidux live cd and tried to access it. It showed up in the storage devices. I clicked on it and it told me to check something. I will go get a screen of the message.

---

### Post by patrickaupperle on 2008-05-01
I got it.

---

### Post by patrickaupperle on 2008-05-01
bump.

---

### Post by odiseo77 on 2008-05-01
Weird... It seems the sidux devs forgot to put some description for this error (which is probably caused by the fact of non having permissions to open storage devices, or by a lack of driver to read/write NTFS). Have you tried installing ntfs-3g, making a mount point for the device and mounting it manually to see which error comes the CLI with? Something like this:

```
su
apt-get install ntfs-3g
mkdir /mnt/sdb1
mount -t ntfs-3g /dev/sdb1 /mnt/sdb1
```

Since for what I've heard sidux is somewhat unstable, I'd suggest you to back up the data on the drive before doing this, just in case.

---

### Post by dptxp on 2008-05-02
check sidux manual. 
[http://sidux.com](http://sidux.com)

You can ask at their forums. Same link.

---

### Post by patrickaupperle on 2008-05-02
I just backed up the backup drive and formatted it ext 2. I have not tried it yet, but it should work now.

---

