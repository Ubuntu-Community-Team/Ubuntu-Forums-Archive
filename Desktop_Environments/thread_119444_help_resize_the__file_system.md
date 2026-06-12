---
title: "help: resize the / file system"
date: 2006-01-19
forum: Desktop Environments
---

### Post by jason2005 on 2006-01-19
ubuntu 5.10  with the following disk partition. 
how to shrink / so that I could create more partitions. 
will boot up to live CD, using gpartd works to resize
the / ? 

thanks.Jason

root@jason:~# fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30017   241111521   83  Linux
/dev/sda2           30018       30394     3028252+   5  Extended
/dev/sda5           30018       30394     3028221   82  Linux swap / Solaris
root@jason:~# df -k
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            237327520   1841712 223430232   1% /
tmpfs                   517616         0    517616   0% /dev/shm
tmpfs                   517616     12588    505028   3% /lib/modules/2.6.12-9-386/volatile

---

### Post by Wolki on 2006-01-19
[QUOTE=jason2005]will boot up to live CD, using gpartd works to resize
the / ? [/QUOTE]

Yes, it should.

---

### Post by az on 2006-01-19
You need to unmount your swap, first.  It is used by default by the live cd.

sudo swapoff -a

---

### Post by jason2005 on 2006-01-19
just tried that.  it works but I run into the following problem:
I tried to resize/enlarge an extended partition. /dev/sda2.
but unable to delate/resize sda2 since that swap is active?

I 've tried  booting  from liveCD, with "noswap"  options
boot: live noswap 

still the swap is active.  how do I pass noswap to the grub? 
thanks. 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30017   241111521   83  Linux
/dev/sda2           30018       30394     3028252+   5  Extended
/dev/sda5           30018       30394     3028221   82  Linux swap / Solaris

---

### Post by Herman on 2006-01-19
I found it hard to do everything I wanted with the Breezy live CD version of GParted too. Although it is very good, especially for Fat32 and probably ntfs resizing, (I haven't got any ntfs to try that out on), GParted on its own CD is a lot better. GParted-livecd-0.1.iso is a 33.1 MB download and it will do what you want without a problem. Download the .iso file and burn it a new CD of its own.
Maybe it's better because GParted on its own live CD is more up-to date than the version on the Breezy live CD, and/or has more of the needed libraries and what-not, I'm not sure. I just know it's great!
And it doesn't require as much RAM out of my computer either, so it has the reserve memory to work a lot better. My smallest and oldest computer only has 128mb and the Breezy live CD used all that and a little of the swap to run Breezy before I even started GParted. Then when I unmounted the swap I couldn't do very much with GParted, the old computer slowed so much it was nearly frozen.
Try GParted on its own CD, you'll love it! (Click on my second sig link) :D (Herman)

---

