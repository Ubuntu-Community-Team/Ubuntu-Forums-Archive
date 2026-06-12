---
title: "Windows will not boot; would GRUB be able to boot it up?"
date: 2009-05-08
forum: General Help
---

### Post by MysticalRiotCandy on 2009-05-08
I'm not too sure where to ask this, but I'm currently working on a friend's laptop that runs XP.  For some reason, it won't boot.  I originally thought that it wouldn't boot because the MBR was broken, so I tried to fix it using a LiveCD and running "$ ms-sys -m" and testdisk.  Both methods have failed to work, and it still will not boot up.  The screen simply displays a blinking underscore line.  The HDD with the Windows boot does have the required bootup files (BOOT.INI, NTDETECT.COM, and NTLDR).  If I installed GRUB to the HDD as the bootloader by placing a small Ubuntu install and set GRUB to automatically load up Windows first, would that solve my problem?

---

### Post by cariboo on 2009-05-08
If you have a Windows install disk, just boot from it and go into the recovery console and use FIXMBR and FIXBOOT

---

### Post by coffeecat on 2009-05-08
> **MysticalRiotCandy said:**
> If I installed GRUB to the HDD as the bootloader by placing a small Ubuntu install and set GRUB to automatically load up Windows first, would that solve my problem?

Yes, in theory. But that would only work if the Windows NTLDR is not corrupted. And if that's the case, you're better off repairing the Windows MBR.

Are you able to get your hands on a Windows XP install CD? Not a hardware manufacturer's restore disc. I mean a genuine MS disc with the MS logo on it. If you can, run both FIXMBR and FIXBOOT from the repair console. Another alternative is to try [Super Grub Disc]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"). If SGD can't boot you into Windows, then preparing a grub partition isn't going to help. There are two Windows entries on the SGD menu - one to boot into Windows, and one to repair the MBR and then to boot into Windows. Neither are very self-explanatory, but they do work, so long as the NTLDR is not broken. 

**Edit:** cariboo907 beat me to it re FIXMBR and FIXBOOT. :)

---

### Post by MysticalRiotCandy on 2009-05-08
I do not have access to a Windows disc.  However, I'm burning a SGD as we speak.  I placed in so-called universal boot files to replace any possible corrupted ones, but it still will not work.  So NTLDR corruption isn't likely.  I'm supposing that the Windows Bootloader is missing.

---

### Post by coffeecat on 2009-05-08
> **MysticalRiotCandy said:**
> I placed in so-called universal boot files to replace any possible corrupted ones, but it still will not work.  So NTLDR corruption isn't likely.

I'm certainly no expert, but I think it's slightly more complicated than copying in the various Windows boot files. I once had a system where all the files were in place and BOOT.INI looked fine, but there was a problem only solved by the use of FIXBOOT.

But good luck anyway.

---

### Post by Don1500 on 2009-05-08
You can download the Ultimate Boot CD ( [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) )(includes SGD) It has FIXMBR and FIXBOOT on it. When I tried to set upa dual boot system the first time I used this to restore Windows a bunch of times before I got it right.

---

