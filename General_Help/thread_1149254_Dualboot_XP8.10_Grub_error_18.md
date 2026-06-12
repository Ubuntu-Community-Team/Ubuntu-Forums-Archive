---
title: "Dualboot XP/8.10 Grub error 18"
date: 2009-05-05
forum: General Help
---

### Post by jaqrah on 2009-05-05
Dammit!  My main box is down.  I am dualbooting XP MCE 2005 SP3 and Ubuntu 8.10. I am running on a Dell Dimension E510.  Was watching a recorded tv program in media center and I looked up and it just hung.  No response from ctrl/alt/del..dead in the water.  I power off/on, get the Dell bios screen, next grub bootloader and then Error 18.

I googled and read a few things but nothing made sense to me(create new /boot partition before primary partition??) and most of it seemed dated from 4 or 5 years ago.  Is there a fix to this that isn't going to make me sweat blood?

**or** does it make more sense to just hit factory restore and try loading a backup image of my C drive...haven't ever had to do to this so any advice for this option would be also helpful.

---

### Post by stretch427 on 2009-05-05
Well I don't know how much help I can be but basically what's happening with a grub error 18 is that the BIOS can't access the boot file. 

If you have a Windows boot CD you could trying booting to that and clicking fixmbr.

Or going into a partitioner( I apologize if I'm being over simplistic) and basically telling it to look for grub in a certain area.

Be careful doing that... And I also recommend if you do. Back up your data ie external hardrive so you don't worry about losing anything... 

Trust me I just lost about 100GB of media the other day by thinking  I knew what I was doing. Dumb.... lol

If you have Q's about partitioning... ask I might be able to help.

Cheers

---

