---
title: "GRUB loading slow"
date: 2005-07-24
forum: Desktop Environments
---

### Post by yengamatic on 2005-07-24
I've just installed ubuntu on a P4@2.8 with WinXP also installed on it in the same hdd.
When i start the computer, GRUB takes a lot of time to load the menu (about 1 minute). It first stops with 'GRUB loading stage1.5' message and then displays another 'GRUB sometext' message before showing the menu. Do you know what can i do to solve that?

---

### Post by Muhammad on 2005-08-07
I have the same problem. :(

---

### Post by drews_blunted on 2005-08-12
Im running a amd athlon 64 3400+ with ubuntu hoary i386 and i have a very slow time loading grub, ive seen it run very fast almost instantly on a 500 mhz pentium 2 so i know its not my system being too slow. hahaha. It would be great if someone here could figure out how to fix this.

---

### Post by pirast on 2005-10-23
If you still have this problem please help solving it:

[https://launchpad.net/distros/ubuntu/+sources/grub/+bug/3245](https://launchpad.net/distros/ubuntu/+sources/grub/+bug/3245)

---

### Post by alainhenry on 2005-10-31
I am not sure this is relevant here, but I had a similar problem caused by my BIOS, which can only boot from partitions in the first part of the HD (I guess it could be the first 64 Gigabyte in my case, but I am not sure).   Installing Breezy at the beginning of my second drive instead of at the end of drive 1 allowed me to have GRUB working correctly.

Alain

---

### Post by bartc on 2005-11-12
[QUOTE=alainhenry]I am not sure this is relevant here, but I had a similar problem caused by my BIOS, which can only boot from partitions in the first part of the HD (I guess it could be the first 64 Gigabyte in my case, but I am not sure).   Installing Breezy at the beginning of my second drive instead of at the end of drive 1 allowed me to have GRUB working correctly.

Alain[/QUOTE]
I have the same problem yengamatic has. I think grub was installed in the MBR, so I guess grub being slow can't be because of this BIOS issue.
Has anyone found a solution yet?

---

### Post by bartc on 2005-11-12
Quote from [http://ubuntuforums.org/showthread.php?t=23230]("http://ubuntuforums.org/showthread.php?t=23230"):
[QUOTE=feneks]Stage 1 is installed at the mbr of the first disk and just boots stage 2 or stage 1.5. Stage 1.5 is neccessary if your boot (or root) partition is behind the first 1024 cylinders of the first disk. The job of stage 1.5 is to find and load stage 2. Stage 2 then searches for the kernel and boots the system. Stage 1.5 is either just at /boot or as a small part at mbr and the rest at /boot.[/QUOTE]
So it does may be caused by the BIOS, as alainhenry suggested.

The BIOS issue doesn't really apply to my case, but it might be related. I have a SATA disk with a WinXP setup, as wel as an IDE disk which contains the ubuntu install. Since I didn't change the drive priority prior to installing Ubuntu, I guess grub was installed on the SATA disk (although I am not sure if grub could know which disk the BIOS boots from, but after I rebooted, grub started instead of NTLoader). So grub might be having trouble finding files on the other disk.

I guess I'll try installing grub on the IDE disk monday morning...

---

### Post by alainhenry on 2005-11-13
For info, 
When I first installed Ubuntu, I also has problems because windows did not recognise the hard drive that was first partitioned and formatted with Ubuntu.  Windows needs a disk formatted by itself in order to wrok properly.  (see [http://www.ubuntuforums.org/showthread.php?t=40197](http://www.ubuntuforums.org/showthread.php?t=40197) for a long discussion on this)

Alain

---

### Post by ciroxyz on 2008-03-05
> **bartc said:**
> Quote from [http://ubuntuforums.org/showthread.php?t=23230]("http://ubuntuforums.org/showthread.php?t=23230"):

So it does may be caused by the BIOS, as alainhenry suggested.

The BIOS issue doesn't really apply to my case, but it might be related. I have a SATA disk with a WinXP setup, as wel as an IDE disk which contains the ubuntu install. Since I didn't change the drive priority prior to installing Ubuntu, I guess grub was installed on the SATA disk (although I am not sure if grub could know which disk the BIOS boots from, but after I rebooted, grub started instead of NTLoader). So grub might be having trouble finding files on the other disk.

I guess I'll try installing grub on the IDE disk monday morning...

I have excatly the same configuration (xp on sata drive, and ubuntu on ide) and the same problem... Seems like grub is trying to "find something" during stage 1.5,
Could it be that it's trying to find xp's bootsector or bootloader. I'm sure grub is installed on IDE since I boot xp by just switching boot sequence in BIOS (I change to sata drive that has xp) and win xp boot loader boots windows.
So, if someone find a solution (probably something needs rewriting in grub itself), post here...
cheers! ):P

---

