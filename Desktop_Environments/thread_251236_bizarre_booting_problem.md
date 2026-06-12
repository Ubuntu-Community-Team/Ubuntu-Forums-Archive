---
title: "bizarre booting problem"
date: 2006-09-05
forum: Desktop Environments
---

### Post by devdsp on 2006-09-05
Hi there

This morning, when I tried to boot my Ubuntu 6.06 box, it gave me bad news:
[INDENT]mount: Mounting /dev/hda1 on root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed : No such file or dir
mount: Mounting /sys on on /root/sys failed: No such file or dir
mount: Mounting /proc on /root/proc failed: No such file or dir[/INDENT]

It's my / partition. That's funny, it worked perfectly yesterday, and I haven't touched the configuration. Grub is fine, /etc/fstab is fine, and the partition is fine. :???: 

I've used several LiveCDs (Ubuntu, Puppy, Slax) and they all can mount /dev/hda1, and fsck.ext3 says it is clean.

Maybe it's related to my /home partition getting crammed? It was full when I tried to boot, but then I freed several GBs.

Any clues? :-k

---

