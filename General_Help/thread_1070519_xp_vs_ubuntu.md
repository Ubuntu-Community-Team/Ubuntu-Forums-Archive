---
title: "xp vs ubuntu"
date: 2009-02-15
forum: General Help
---

### Post by tarek alaa on 2009-02-15
hi 
i have a very serious problem..... when i setup ubuntu,my xp version didn't work so i said not a problem i will set it up back again but when i did, it couldn't read ubuntu drive here comes the problem ubuntu didn't open back as well and i can't read this drive now on xp and ofcourse i can't setup ubuntu again  could any one tell me what's wrong   thanx

---

### Post by Sprut1 on 2009-02-15
> **tarek alaa said:**
> hi 
i have a very serious problem..... when i setup ubuntu,my xp version didn't work so i said not a problem i will set it up back again but when i did, it couldn't read ubuntu drive here comes the problem ubuntu didn't open back as well and i can't read this drive now on xp and ofcourse i can't setup ubuntu again  could any one tell me what's wrong   thanx

Can't say I quite understood you, but if its the case that you installed Windows XP after Ubuntu most likely the MBR is "broken" - XP doesn't care about anything but itself.

---

### Post by tarek alaa on 2009-02-15
> **Sprut1 said:**
> Can't say I quite understood you, but if its the case that you installed Windows XP after Ubuntu most likely the MBR is "broken" - XP doesn't care about anything but itself.

ok but now i have 20GB drive i can't read on xp what could i do?

---

### Post by Sprut1 on 2009-02-15
Try to explain your problem again, I'm not sure what you're asking. If Ubuntu is installed on the 20gig drive WinXp won't be able to read it, format it to NTFS/FAT32.

---

### Post by Kevbert on 2009-02-15
Once you re-install Windows the Master Boot Record will be overwritten. To get your PC to boot both Windows and Ubuntu you need to restore the Grub bootloader. Please take a look at [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351"). The reason that you can't see the Ubuntu patition in Windows is that it cannot see ext3 (the default format that linux uses) drives.

---

