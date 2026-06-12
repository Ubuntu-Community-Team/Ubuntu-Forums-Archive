---
title: "How to boot into Ubuntu after Dell PC Restore?"
date: 2008-01-17
forum: Dell  Ubuntu Support
---

### Post by thesn00zer on 2008-01-17
Hi,

I'm kind of new to Ubuntu and dual-booting. I had a problem with Windows booting (it would hang on a driver load), so I decided to use Dell PC Restore to restore the XP partition to how it was when it was shipped (it was smart and left my Ubuntu partition alone). When I installed Ubuntu, it disabled the Ctr + F11 shortcut to get into PC Restore, so I had to download a program to fix it, and now Windows just starts up with no boot menu.

Anyway, my question is: is there any way that I can keep the PC Restore shortcut while being able to boot Ubuntu? Pressing a key at startup would be fine if a boot menu is not possible. Can this be done with a Windows boot menu?

Thanks!

---

### Post by thesn00zer on 2008-01-18
anyone????

---

### Post by Aearenda on 2008-01-18
If your Dell is like mine, the factory Windows XP installation has a non-standard master boot record (MBR) that is used to enable the Dell recovery process. On normal boots it simply transfers control to Windows in the main partition. There are two more hidden partitions that the Dell recovery process needs, leaving one spare slot in the partition table for an extended partition, which is where Ubuntu and its swap go.

When you installed Ubuntu, you likely chose to let it overwrite the MBR with Grub. This disabled the Ctrl/F11 check, but allowed you to dual boot using Grub's menu. I'm assuming this is what you did hereafter, but if you didn't, then let us know what you did instead - don't just follow the instructions I'm going to point you to regardless. So, if I am right and you are happy to go back to the same situation, you can simply re-install Grub from the Ubuntu installation disk. The instructions to use depend on whether you are using the Live CD (which launches you into a running Ubuntu system off the CD) or the Alternate CD (which takes you straight into an installer for Ubuntu, with recovery options). You need to know which partition you originally installed Ubuntu into, which is the hard part. The thread at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) tells you how to do it with the live CD, which is what you probably have. 

The better way to do it, which would keep your ability to do CTRL/F11 again, is to install Grub in Ubuntu's partition, leaving the MBR untouched. You then have to copy the partition's boot sector to a file in the Windows partition, and tell Windows XP's loader about how to start Ubuntu. This isn't hard, but it is a bit fiddly, and if you are unsure of your ability to recover or have no backups then you shouldn't try it. There's a long thread about it at [http://ubuntuforums.org/showthread.php?t=56723](http://ubuntuforums.org/showthread.php?t=56723).

I hope this helps. There is a lot of material on these forums and on the internet about how to proceed in this kind of situation, the hard part is sifting the good stuff out from the not-so-helpful. Please let us know how you get on.

---

### Post by sniper9xm on 2008-01-21
Hello I made a mistake I installed ubuntu and I lost xp and when i try pressing curl+F11 nothing happens

---

### Post by Aearenda on 2008-01-22
sniper9xm: You have to use Ctrl/F11 at exactly the right moment when the PC boots - see the Dell doco that came with your machine for details. Note that this will wipe out everything that you have done before on Windows XP; it might be better to see if you can recover less destructively.

Your next step depends on what does work - you didn't say whether Ubuntu works or not. 

It also depends on how you installed Ubuntu - did you ask it to resize the existing XP partition, or did you ask it to use the entire disk?

---

