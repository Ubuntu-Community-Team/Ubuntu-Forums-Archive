---
title: "kernel support for aes-cbc-essiv:sha256 cipher"
date: 2009-03-26
forum: General Help
---

### Post by lriis on 2009-03-26
Hi,

Trying to use cryptsetup:
```
# cryptsetup -y luksFormat /dev/sda3

WARNING!
========
This will overwrite data on /dev/sda3 irrevocably.

Are you sure? (Type uppercase yes): YES
Enter LUKS passphrase: 
Verify passphrase: 
Command failed: Failed to setup dm-crypt key mapping.
Check kernel for support for the aes-cbc-essiv:sha256 cipher spec and verify that /dev/sda3 contains at least 133 sectors
```

I have loaded aes,cbc, sha256 and dm-crypt. What else do I need to do to get the cipher support I need?

This is on a fresh Jaunty install... Linux 2.6.28-11-generic #37-Ubuntu SMP Mon Mar 23 16:40:23 UTC 2009 i686 GNU/Linux

---

### Post by lriis on 2009-03-26
Nevermind....found the problem

---

### Post by [3w`Sparky] on 2009-06-19
any chance of sharing this infomation

---

### Post by darsu on 2009-08-28
I had the same problem; loading some kernel modules fixed it:
sudo modprobe cryptoloop
sudo modprobe dm_crypt

---

