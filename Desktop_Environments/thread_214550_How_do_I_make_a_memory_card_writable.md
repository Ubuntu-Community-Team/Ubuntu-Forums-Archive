---
title: "How do I make a memory card writable?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by allanlewis on 2006-07-12
](*,) 

Hi,

I've been trying in vain for some time to make the memory card in my mobile phone (cellphone for all you Yanks out there ;) ) writeable under Ubuntu. It appears under WinXP as a standard USB "mass storage" device, i.e. similar to a USB flash disk. I've messed around with the "mount" command but I can't get anywhere. How exactly do I make it automatically mount as writeable whenever I plug it in?

Thanks in advance.

---

### Post by lamego on 2006-07-12
If your memory card has an NTFS partition you can't write on it from Linux. NTFS is only supported in read-only mode. You would need to recreate it as FAT.

---

### Post by allanlewis on 2006-07-13
> **lamego said:**
> If your memory card has an NTFS partition you can't write on it from Linux. NTFS is only supported in read-only mode. You would need to recreate it as FAT.
No, it's definitely a FAT-type partition (i.e. FAT or FAT32). I've heard that FATx partitions often get corrupted on removable devices - is this true? If so, is it worth re-formatting my card? (It's a 1GB Memory Stick Pro Duo, if it matters.)

---

### Post by philippe_carlo on 2006-07-13
For some reason, your card is not recognized as a block device, it seems. Can you plug it in and then post the output of 

dmesg | tail?

---

### Post by allanlewis on 2006-07-13
> **philippe_carlo said:**
> For some reason, your card is not recognized as a block device, it seems. Can you plug it in and then post the output of 

dmesg | tail?
Sorry, I think I misrepresented my problem slightly. My device is recognised and mounts read-only successfully, but I can't get it to mount read/write.

UPDATE:
It seems that the new kernel has solved my problem! It now mounts read/write perfectly :)

---

### Post by philippe_carlo on 2006-07-13
Good for you!

---

