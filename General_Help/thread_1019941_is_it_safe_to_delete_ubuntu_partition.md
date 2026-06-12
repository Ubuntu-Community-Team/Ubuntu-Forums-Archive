---
title: "is it safe to delete ubuntu partition"
date: 2008-12-23
forum: General Help
---

### Post by yurib on 2008-12-23
hello,

i have both xp and ubuntu on my laptop, using grub to select which one to start at boot, i wanna rearrange my partitions, is it safe to just delete my ubuntu partition ? will i still be able to boot xp ?

---

### Post by howefield on 2008-12-23
If you delete your Ubuntu partition you'll still be able to boot XP, but you'll still have the grub menu with Ubuntu on it. (assuming you installed Ubuntu after you installed XP)

---

### Post by 10nitro on 2008-12-23
Is grub installed on the same partition as Ubuntu? (yes, unless you did it yourself)  If so, this will make your system unbootable.

---

### Post by oilchangeguy on 2008-12-23
> **yurib said:**
> hello,

i have both xp and ubuntu on my laptop, using grub to select which one to start at boot, i wanna rearrange my partitions, is it safe to just delete my ubuntu partition ? will i still be able to boot xp ?

if you delete the ubuntu partition, you'll need to use your windows install cd, to fix the windows boot record. boot from the cd, and when it loads select r to enter the repair console. select your windows install, usually 1, then type the admin password, if none press enter to bypass the prompt. then type fixboot and press enter, then type fixmbr and press enter, then type exit and press enter. and windows should load fine.

---

### Post by yurib on 2008-12-23
sheesh... is there a way to do it without going through all that ?
can i somehow uninstall grub before deleting the partition so that xp boots like it always does without messing around with the repair console ?

---

### Post by 10nitro on 2008-12-23
> **yurib said:**
> sheesh... is there a way to do it without going through all that ?
can i somehow uninstall grub before deleting the partition so that xp boots like it always does without messing around with the repair console ?

You need a bootloader.  If you delete GRUB, you will need a new one.  oilchangeguy described (re)installing NTLDR, the Windows XP bootloader

You can install a GRUB on a new partition in Ubuntu fairly easily.

You will need gparted for this (sudo apt-get install gparted)

If you have any unpartitioned space, create a small ext2 partition (10MB is more than enough)(use gparted for this)

Mount the new partition. Know where it is.

type the commands:
```

sudo mkdir */path/to/new/partition*/boot/
sudo cp -v -r /boot/grub */path/to/new/partition*/boot/
sudo grub
grub> find /boot/grub/stage1
    (hd*X*,*Y*)
    (hd*X*,*Y*)

```
Note the output here. X is the hard drive, Y is the partition.  One of these will be the Ubuntu partition, one is the new partition.  These are GRUB addresses, not Linux addresses.  In Linux "(hd0,5)" is "/dev/hda6"  (or sda6 if it is a SATA drive),  "(hd1,3)" is "/dev/hdb4". Anyway, figure out which one is the drive we just created, and type:
```

grub> root (hd*X*,*Y*)
grub> setup (hd*X*)
grub> quit
```

Now, you have GRUB on a separate partition, and it is safe to delete the Ubuntu partition.

---

### Post by oilchangeguy on 2008-12-23
> **yurib said:**
> sheesh... is there a way to do it without going through all that ?
can i somehow uninstall grub before deleting the partition so that xp boots like it always does without messing around with the repair console ?

if you can't take the time to go through a few simple steps to get the windows bootloader installed, maybe you should just leave ubuntu. so you'll still have grub. otherwise you get to follow the steps i outlined. there's no way around it. if you want to fix windows. go to [www.microsoft.com](www.microsoft.com) and search fixmbr, you'll get the same info.

---

### Post by Jammanuser on 2008-12-23
> **yurib said:**
> sheesh... is there a way to do it without going through all that ?
can i somehow uninstall grub before deleting the partition so that xp boots like it always does without messing around with the repair console ?

I would have recommended hiding your XP partition, to begin with, when installing Ubuntu 8.10, and making sure that Grub went to the partition that Ubuntu was installed on, instead of to the MBR! But now that you have already overwritten your XP bootloader, you will need to rebuild it no matter what, like oilchangeguy said... ;)

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by 10nitro on 2008-12-23
If you delete the partition, then use the Ubuntu CD to reinstall Ubuntu, the new instillation will detect Windows XP, but the system won't be bootable (from the hard drive) until you install a new boot loader, which the Ubunto CD does.

> **oilchangeguy said:**
> if you can't take the time to go through a few simple steps to get the windows bootloader installed, maybe you should just leave ubuntu. so you'll still have grub. otherwise you get to follow the steps i outlined. there's no way around it. if you want to fix windows. go to [www.microsoft.com](www.microsoft.com) and search fixmbr, you'll get the same info.

He didn't say he wanted to stop using Ubuntu, he said he wanted to rearrange his partitions.

> **Jammanuser said:**
> I would have recommended hiding your XP partition, to begin with, when installing Ubuntu 8.10, and making sure that Grub went to the partition that Ubuntu was installed on, instead of to the MBR! But now that you have already overwritten your XP bootloader, you will need to rebuild it no matter what, like oilchangeguy said... ;)

Cheers! :popcorn:

-Jam man

:guitar:

So you would have NTLDR chainload into GRUB?  I use GRUB even on machines with only Windows, it's just better.  I Always give GRUB it's own partition, though, to make it operating system independent, which is the idea of GRUB.

---

### Post by oilchangeguy on 2008-12-23
> **10nitro said:**
> If you delete the partition, then use the Ubuntu CD to reinstall Ubuntu, the new instillation will detect Windows XP, but the system won't be bootable (from the hard drive) until you install a new boot loader, which the Ubunto CD does.



He didn't say he wanted to stop using Ubuntu, he said he wanted to rearrange his partitions.



So you would have NTLDR chainload into GRUB?  I use GRUB even on machines with only Windows, it's just better.  I Always give GRUB it's own partition, though, to make it operating system independent, which is the idea of GRUB.

well if the op wants to delete the ubuntu partition it's a safe bet they want to stop using ubuntu. and expand the windows partition to use the entire drive.

---

### Post by Jammanuser on 2008-12-24
> **10nitro said:**
> 
[COLOR="Red"]So you would have NTLDR chainload into GRUB?[/COLOR] I use GRUB even on machines with only Windows, it's just better.  I Always give GRUB it's own partition, though, to make it operating system independent, which is the idea of GRUB.

No...so NTLDR wouldn't be overwritten when Ubuntu is installed, along with Grub! :) Of course, I meant that he should have used Grub to dual boot, not that he should have used NTLDR to chainload into Grub (I don't even think its possible, btw!)...

If he had done that (i.e. hiding the XP partition, before installing Ubuntu and Grub), I figure that NTLDR would have remained...only not as the default bootloader! And when he got rid of Ubuntu, his XP bootloader would now become the default bootloader, in place of Grub! :popcorn:

Cheers! :popcorn:

-Jam man

:guitar:

---

### Post by balaknair on 2008-12-24
See this thread
[HowTo: Remove Ubuntu (& Restore Windows)]("http://ubuntuforums.org/showthread.php?t=508927")

---

