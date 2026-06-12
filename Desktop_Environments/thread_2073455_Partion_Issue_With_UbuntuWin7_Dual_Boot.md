---
title: "Partion Issue With Ubuntu/Win7 Dual Boot"
date: 2012-10-19
forum: Desktop Environments
---

### Post by marque on 2012-10-19
I am dual booting with Ubuntu 12.04 and Windows XP.

Both systems have been installed and are working and I'm using GRUB2 for booting.

Basically, I am using two separate hard drives, one designated for ubuntu on one for Windows.

The windows installer did something that I haven't seen before and do not understand.  It required that I allocate a small partition before it would setup and it created an 8M fat16 partition on the disk that I've designated for ubuntu.  This is apparently something different than the System Reserved partition that Windows has always required in addition to the space for the OS itself.

Can someone explain to me the purpose for this partition?  Is it essential for WinXP to boot?  Can I just delete it? Or at least move it to the Windows disk?

---

### Post by oldfred on 2012-10-19
Is this XP or Windows 7. I have seen Windows 7 put its boot partition on the drive that is the boot drive in BIOS. Or when installed to a second drive it may install the 100MB boot partition on the first drive.

May be best to post this just to see what is where. Which drive is set as boot drive in BIOS?

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by marque on 2012-10-19
Windows XP

Link to boot-repair results:
[http://paste.ubuntu.com/1290492/]("http://paste.ubuntu.com/1290492/")

---

