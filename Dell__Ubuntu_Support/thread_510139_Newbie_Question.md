---
title: "Newbie Question"
date: 2007-07-26
forum: Dell  Ubuntu Support
---

### Post by ETZepplin on 2007-07-26
I have a Dell that I'm interested in trying this out on.... However I'm not all that computer savvy, and am nervoust to whipe XP off my system and put this on, lest I can never get anything working on it again. Can I purchase another harddrive, and have the Ubuntu on that, and boot that instead, at least until I get used to this, and know if I want to keep it? I would do the partition thing, but I don't want to loose all the stuff on my harddrive now, and I'd rather just leave it alone and be able to try this out.... is that possible?

Thanks,
Erik

---

### Post by maldojr88 on 2007-07-26
im kind of not clear as to wat is is that you want

---

### Post by pbcartwright on 2007-07-26
when you start the install process, you will get to the partitioning section. It will ask you if you want to make your existing partition smaller, use all free space, or use another drive/partition. You can shrink your NTFS Windows partition and have both XP/Linux on the same drive, without messing with any of your existing information..

---

### Post by Dellfan on 2007-07-26
You certainly could add another hard drive and load Ubuntu there. However, you will have to modify the MBR (master boot record) to be able to choose to boot Ubuntu or Windows. This would give you a dual boot setup with Windows on one disk and Ubuntu on the second, with the only change to the Windows disk being the MBR.

Really, using the installer to shrink your current Windows partition and install Ubuntu in the freed up space is simple and safe.

If you are ultra phobic you could simply remove your Windows hard drive, install a new one and load Ubuntu there. It would be more work, and require swapping hard drives to go back and forth. If you want to explore this option there are hard drive caddies that basically allow you to plug them in and out.

---

### Post by WinterWeaver on 2007-07-26
You can also use the LIVECD to try it out. Unfortunately you will be restricted with the live CD, and it loads quite slow... but it's a good way to familiarize yourself a little bit with the interface and general programs.

Thereafter, as suggested, you can create a second partition on your current drive. you will then have a dual boot option (windows or ubuntu)

Alternatively, if you have the cash to space, buy the second drive and use that for your ubuntu partition.

all is up to you though ... just remember to make backups no matter what you choose to do... that's the best way forward :)

WW

---

