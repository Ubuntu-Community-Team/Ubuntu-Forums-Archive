---
title: "Formatted Windows Drive withWubi"
date: 2009-04-28
forum: General Help
---

### Post by Udi on 2009-04-28
Hi,

Well, I did something dumb, I had Linux Mint installed with Wubi.
And I had Windows installed.

Windows installed in C:, linux Mint in drive Z:

**I formatted drive C:** [I used partition manager in linux for that]
and when I restarted my linux I get the next error:
"Reboot and select proper Boot device
or Insert Boot Media in Selected Boot Device.."

Now, I have some serious stuff in my linux, so I really don't want to format it and reinstall linux,
In the formatted Windows Driver I have lots of movies, music and pictures, this I can deleted but I really rather to find some other solution.

So.. there is any way to make a boot of my Mint?

Thank you all.

---

### Post by damis648 on 2009-04-28
Unfortunately, everything in Windows is gone if you in fact did format Windows drive C:... If you did also install Linux Mint via Wubi, that is all gone too, as Wubi just sticks your Linux installation onto the Windows partition. Next time, do a full install of Linux if you plan to seriously use it, otherwise stuff like this can happen. As a formality, could you boot up a LiveCD and open a terminal and post the output of:
```
sudo fdisk -l
```

---

### Post by Udi on 2009-04-29
gone? even if Wubi installed in a different partition?
but the data has to be there, cuz I managed to use Linux Mint after the format.

Here the output you wanted:
```
invalid option --1
```

---

### Post by damis648 on 2009-04-29
Ah well if it was installed in a different partition it still might be possible.

Could you try that command again, that was an 'l' as in the letter L, not a one.

---

### Post by Udi on 2009-04-29
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5100    40965718+   7  HPFS/NTFS
/dev/sda2            5101        9092    32065740    f  W95 Ext'd (LBA)
/dev/sda3            9093       14593    44186782+   7  HPFS/NTFS
/dev/sda5   *        5101        9092    32065708+   7  HPFS/NTFS

```

I installed Windows again,
I think if I restore the boot.ini of Windows, I can access my Mint.

You have better idea.. ?

Thank you!

P.S
I flagged my Linux partition as "boot", I think this is why you see 2 boot partitions.

---

