---
title: "[SOLVED] Help with hard drives"
date: 2009-01-01
forum: General Help
---

### Post by Tyke91 on 2009-01-01
I've been using Ubuntu for some time now, and just bought a brand new terrabyte hard drive (hurray storage space!).

The boot sector on my windows partition was corrupted and my ubuntu partition was getting very full so I decided that it would be a good idea to reinstall everything when I added the new hard drive. 

The reinstall of windows was good and the ubuntu install went beautifully, but I've run into some issues.

1st issue, ever since I put the hard drive in, I now get a message when I start up my computer (after the BIOS loads) that says that I have no RAID devices configured, lists the two hard drives, and then asks me to continue by hitting F1 or enter the BIOS with F2.

I haven't found any option in the BIOS to fix this, and when I hit F1, it automatically skips to the windows install without going through GRUB, although when I use the live CD I see that I have indeed installed ubuntu on this partition and that GRUB HAS been installed.


right now my partition setup is as follows

Drive - Type   - Size
sda    - Fat32 - 160 GiB (for extra media storage)
sdb1  - NTFS -  195 GiB (for windows)
sdb2  - extended:
sdb5  - ext3 - 732.95 GiB (root)
sdb6  - swap - 2.94 GiB


If you need any more system info please ask... I'm not quite sure exactly what information to give in this situation, I've never had to deal with 2 hard drives before.

---

### Post by Tyke91 on 2009-01-01
So, I fixed the problem with the system pausing and asking me to press F1 by messing with the BIOS, but there's still the issue with GRUB. It seems as if I have two separate problems.

---

### Post by Tyke91 on 2009-01-01
I've tried the standard grub restoration and I still can't get it to work

what I did from inside a live CD
```

$ sudo grub
>> find /boot/grub/stage1
(hd1,4)
>> root (hd1,4)
>>setup (hd0)
>>quit
$ sudo reboot

```

nothing happened on reboot, it went straight to windows after removing the CD.

---

### Post by Tyke91 on 2009-01-01
Solved ^^

It turns out that my problem was a misunderstanding of how GRUB works.

I had set my bios to boot to my new hard drive first, because this was where ubuntu was installed and I thought that It would install grub there. Grub was instead installed to the first hard drive, booting from that worked fine :)

---

