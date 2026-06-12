---
title: "i cant see my 2nd ntfs storage drive ubuntu 8.10"
date: 2009-01-24
forum: General Help
---

### Post by SniperDaws on 2009-01-24
ok im a complete n00b to Ubuntu and so far everythings been going great, im using it on Vista with the latest Sun xVM Virtualbox and the only problem i have upto now is i cant see my 2nd 250GB Sata2 which contains all my music, films and pics. the drive is plugged into an intel sata2 port and ahci is enabled.

Thanks i hope you can help me :):popcorn:

---

### Post by cariboo on 2009-01-24
Can you open an Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

and paste the output in your next post.

Jim

---

### Post by SniperDaws on 2009-01-24
Thanks mate, heres what it came up with.


andy@LinuxLive-PC:~$ sudo fdisk -l
[sudo] password for andy: 

Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006f3ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         993     7976241   83  Linux
/dev/sda2             994        1044      409657+   5  Extended
/dev/sda5             994        1044      409626   82  Linux swap / Solaris
andy@LinuxLive-PC:~$ 


:)

---

### Post by SniperDaws on 2009-01-25
Bump :)

---

