---
title: "Ubuntu 8.10 &amp; Vista SP1 Dual-Boot, Vista MBR Corrupt?!"
date: 2009-01-07
forum: General Help
---

### Post by nightfire117 on 2009-01-07
Hey all, been a while since I used the forums but after exhaustively looking everywhere I couldn't find quite an approximation to the issue I've been having.

**Summary:**
Vista installed on one HD, Ubuntu installed on another HD over top of XP. GRUB doesn't show Vista, and I tried adding it, but BOOTMGR failed. Vista Repair Disk doesn't detect the drive either but can browse it.

**Details:**
I had XP and Vista on two separate hard drives. XP was my primary hard drive, Vista my secondary. And a third HD, which I use to store media (music, videos, docs, pics, etc.). I installed Ubuntu on the XP hard drive. (I previously had an Ubuntu 8.04 install 15 GB partition on the Media drive, but I installed Vista and it overwrote GRUB or something and I just never bothered to fix it.) Now GRUB loads up, Ubuntu works and even detects the old install from the other hard drive. But guess what? No Vista on the list. >_<

So I added Vista to my GRUB list (forgot how I did it), it's apparently on (2,0) because I only have (1,x), (2,x), and (3,x). So I boot from it and immediately it says "BOOTMGR is missing. Press CTRL + ALT + DEL to restart." So I loaded the DVD for Vista in and rebooted. Went to the Repair options, and when you select your drive there are *no* options. I *know* the drive works just fine - all of them do - because I even browsed them all, trying to find out wth "Load Drivers" could do, and even running Firefox off of the Vista HD even though I figured it wouldn't work.

Anyways... some help would be great. I love Ubuntu and its community (I mean, who else would read this long nonsense?), but, I really need to get back to that Vista install.

~Night

_______________________________________________________________________

P.S. If you're wondering: I can't quite make the full switch to Ubuntu - believe me, I've tried time and time again, but each time there's that *one* app that noone can yet replace. And then another. And another. And then the awful DVD playback quality and interlacing issues at the cost of more quality I've seem to have been getting which is probably fixable.

---

### Post by cariboo on 2009-01-07
Vista has to have it's bootloader on the first partition of the first hard drive, just like XP. I would suggest installing Vista on the first hard drive, then install Ubuntu on the second hard drive, and let the installer install grub in the mbr of the first hard drive.

Jim

---

### Post by nightfire117 on 2009-01-08
> **cariboo907 said:**
> Vista has to have it's bootloader on the first partition of the first hard drive, just like XP. I would suggest installing Vista on the first hard drive, then install Ubuntu on the second hard drive, and let the installer install grub in the mbr of the first hard drive.

Jim

I see... thanks, I wasn't aware of that. So would just changing the jumpers work...? Cause the Windows recovery disk isn't seeing "C:\" as the Vista drive, which it sees as "D:\" and I don't quite feel like reinstalling right now since I need stuff on my other hard drive.

~Night

---

