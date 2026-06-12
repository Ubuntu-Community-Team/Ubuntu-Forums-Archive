---
title: "Dual Boot - Windows XP Boots Slowly Using  GRUB in /boot"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Razor X on 2006-08-31
Ok, so I successfully installed Windows XP, and it booted FAST. Then I installed Ubuntu with GRUB in a separate 50 MB ext3 /boot partition. Now when I boot XP using GRUB, the windows XP logo boot screen appears for 10-15 seconds longer than it did before.  

I think GRUB is slowing it down because I reinstalled Windows (which turned off GRUB) and now XP boots like lightning again. Of course, now I can’t dual boot unless I restore GRUB and settle for the slowness.
  

I thought GRUB was supposed to be awesome…Anyone have any ideas about this? Or alternatives?
  
Thank you!

---

### Post by lha on 2006-09-01
> **Razor X said:**
> Ok, so I successfully installed Windows XP, and it booted FAST. Then I installed Ubuntu with GRUB in a separate 50 MB ext3 /boot partition. Now when I boot XP using GRUB, the windows XP logo boot screen appears for 10-15 seconds longer than it did before.  

I think GRUB is slowing it down because I reinstalled Windows (which turned off GRUB) and now XP boots like lightning again. Of course, now I can’t dual boot unless I restore GRUB and settle for the slowness.
  

I thought GRUB was supposed to be awesome…Anyone have any ideas about this? Or alternatives?
  
Thank you!

Grub *is* awesome. :p 

The easiest solution I can think of is to install Grub into the boot sector of a primary partition (not into MBR) and then use [BootPart]("http://www.winimage.com/bootpart.htm") to add Grub into Windows' boot menu.

---

### Post by Razor X on 2006-09-06
I don’t know why I’m reviving this topic….but I had a frustrating day that day because I was going on windows re-install number 3 or 4. Anyway, I think GRUB is awesome, and I think that the Windows boot time just slows down as soon as one starts installing drivers and updates and all. So I’m just gonna leave it alone…



  Maybe your idea would speed it up...I may run a test in the future. 



Thanks for your help though!

---

