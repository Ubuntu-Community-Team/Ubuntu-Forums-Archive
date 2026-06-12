---
title: "automount"
date: 2005-03-23
forum: Desktop Environments
---

### Post by DeltaHuey on 2005-03-23
Hello,

I'm not sure if this is a Kubuntu specific question, but here we go!

I have ubuntu installed on my laptop.  If I plug usb drives they magically appear.  This is ubuntu warthog (4x?).

I have kubuntu Hoary 5.04 on my new machine.  If I plug usb drives in they get detected and show up under storage media (media:/), but if I click on it I get a mounting error that /dev/scd1 (I think) isn't in /etc/fstab or /etc/mtab.  I am under the impression that you no longer need to add removable drives like this to the fstab file (I don't know what mtab is btw!).  I never added this on my laptop, so I'm a bit stumped.

Also, the current drive has 4-5 partitions.  I can only get to the one kubuntu is installed on.  If I click on a different partition under the storage media (media:/) it gives me the same error about fstab and mtab.

Any help is appreciated!  Thanks :)

---

### Post by techlord on 2005-03-23
this is a known issue with automounting and you should install pmount as a workaround

---

### Post by swatch123 on 2005-03-24
Is usbhd drive reading and writing good,and not stopping and waiting?

---

