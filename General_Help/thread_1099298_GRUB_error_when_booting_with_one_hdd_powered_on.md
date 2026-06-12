---
title: "GRUB error when booting with one hdd powered on"
date: 2009-03-18
forum: General Help
---

### Post by Sgtblades275 on 2009-03-18
I originally had Windows XP Pro installed alone then got Ubuntu 8.10 Intrepid Ibex and installed it. Everything went perfect. I had an excellent dual-boot machine. After a while, I decided to get rid of Windows because it was just causing more problems than it was fixing. I couldn't remove Windows through Windows, so I manually deleted all Windows files and wrote over the partition and re-partitioned the Windows drive. Now, that drive is set to NTFS and works fine. But, when I try to boot my machine with just that drive so I can reinstall Windows XP Pro (I miss my games) it gives me a GRUB boot error after I set it to boot from CD. It just says error 21 every time. It also does the same whenever I just try to load up Ubuntu through the larger drive alone. I have it set to boot normally, which should boot from the hdd, but it gives me the same exact error. Now, when they are both connected, I can get on Ubuntu, but it doesn't allow me to install ANY OS. Not even go into the Ubuntu 8.10 LIVE CD options. Just says Hit F1 to retry or F2 to go to System Setup when I hit boot from CD.

What I would like to do is:
1 fix GRUB to be used on both drives when the drives themselves are used individually
OR
2 overwrite GRUB with DOS (I'm just more used to DOS)

Any ideas as to fix this will be very helpful.

---

### Post by ruel- on 2009-03-18
Error 21 means :
"
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name
refers to a disk or BIOS device that is not present or not recognized by the
BIOS in the system.

try:
[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8978](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/8978)
[http://osdir.com/ml/boot-loaders.grub.bugs/2003-02/msg00080.html](http://osdir.com/ml/boot-loaders.grub.bugs/2003-02/msg00080.html)

---

### Post by Sgtblades275 on 2009-03-22
thanks man. Still looking over the links. There's a lot to 'em

---

