---
title: "won't load"
date: 2006-09-02
forum: Desktop Environments
---

### Post by Hans5849 on 2006-09-02
Well, it took me a while but i finally got grub to run, but now when i try to load ubuntu it tells me that it can't find the partition, but i loaded windows fine. My system has a few hard drives (over 1TB) and the drive that im trying to load off of is /dev/sdd- partition 1 for windows, partition 8 for root, and partition 7 for boot (swap is 2 if that matters).

This is what my grub.conf looks like (thank god for the ext2 for windows driver)

```

default 4
timeout 30

title		Ubuntu, kernel
root		(hd3,8)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/sdd8 ro quiet splash
initrd		/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd3,8)
kernel		/vmlinuz-2.6.15-26-386 root=/dev/sdd8 ro single
initrd		/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd3,8)
kernel		/memtest86+.bin 
boot

title		Windows XP
rootnoverify	(hd3,0)
makeactive
chainloader +1

```

please note that i've tried hd3 from 6-8 to see if i could get it to work, but nothing did not even (hd3,7)

---

### Post by Crooksey on 2006-09-02
Look in your /boot directory and /grub, and type the full location of the images.

---

### Post by Hans5849 on 2006-09-03
i coppy-pasted the files so they were in the / and /grub directories so it should of found something, but nothing worked.

---

### Post by maniacmusician on 2006-09-03
hey hans

i was thinking about getting more drives as well, and am wondering about your setup. are your drives IDE? I didnt know how many drives at once IDE can handle. and i didnt really want to mess with other types as i dont have much experience with them.

---

### Post by Hans5849 on 2006-09-03
I have 4 SATA Drives, 2 IDE DVD Drives, and 1 IDE Drive (in route here).

I can have up to a max of 4 SATA and 4 PATA drives, but i have to run it in a special mode in my bios to get it to work with that many drives and that mode isn't compatible with windows 98. Which makes me think that might be causing the problem, maybe i should try the gentoo genkernel to see if it will work that way.

---

