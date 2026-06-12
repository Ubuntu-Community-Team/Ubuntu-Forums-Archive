---
title: "Flash Stick"
date: 2009-04-03
forum: General Help
---

### Post by ub007 on 2009-04-03
I'm trying to format a USB flash disk,which is then to be used to PXE boot from a server.

> cat /proc/partitions

major minor  #blocks     name
  65      80       1016125    sdv
  65      112           1475    sdx

the sdv and sdx confuses me a bit,but the flash stick has a floppy option as well,mayb thats reasin the 'v' n 'x' .....not sure...

I tried

> fdisk /dev/sdv
d
w

> fdisk /dev/sdx
d
w

When i try to PXE boot,it says media incorrect,please insert new media and hit any key...

also tried an alternative approach

> dd if=/dev/zero /dev/sdv bs=512 count=1
dd if=/dev/zero /dev/sdx bs=512 count=1

still same issues....


what am i missing here?How do i get this flash disk to a clean state....The reason for trying this is cz although the sub stick appears brand new,theres something on it that prevents it from being used in the network boot process and shows the error msg

plz help

Cheers
David

---

### Post by Seiji338 on 2009-04-03
I don't know about the rest but the dd command is missing a little bit: ```
dd if=/dev/zero **of=**/dev/sdv bs=512 count=1
```

---

