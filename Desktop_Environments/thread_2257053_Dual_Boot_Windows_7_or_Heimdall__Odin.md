---
title: "Dual Boot Windows 7 or Heimdall / Odin"
date: 2014-12-16
forum: Desktop Environments
---

### Post by jcllings on 2014-12-16
I've installed Windows 7 on an old drive and slipped the old drive into the machine. If I set the Bios to boot from it, it boots fine.  
How can I add it to the Grub menu so that I don't have to fiddle with the Bios?

Having to do this makes me sick BTW, but I can't get Heimdall to work and I can't get Odin to work on a VM. 
Samsung is the worst thing about Samsung devices. :-/

Any of the following would be acceptable: 

1. A solution that gets Hiemdall to work against a Samsung Galaxy Note 4 and a Galaxy 10.1 tablet. <-- This one is ideal but it's my understanding that there's a bug that prevents. 
2. A solution that gets Odin to run on a VirtualBox instance of Windows 7 or 8. I don't have XP. 
3. WAS A solution that adds a Windows 7 (installed on a different physical hard drive) partition to Grub but I hate the idea of having to touch UEFI so much I just can't bring myself to do it.  Nevermind this option.

---

### Post by oldfred on 2014-12-16
Are Windows and Ubuntu both installed in BIOS boot mode, not UEFI? Or both UEFI?

This will add another install of any system to grub menu if in same boot mode.
sudo update-grub

But if not in same boot mode you can only boot from UEFI/BIOS boot menu or perhaps one time boot key like f10 or f12, but varies by system. Some require settings change to turn on/off UEFI or BIOS modes.

---

### Post by jcllings on 2014-12-16
Nevermind on the boot issues. UEFI is such a PITA that I've decided I'll just change the boot order in the BIOS when I need to run that most hated of OS's. :-(
UEFI being a perfect example of WHY people came together and wrote thier own OS in the first place.  
GOD I hate WinBLOWs.

What I found was that Ubuntu was installed in UEFI mode but it was disabled (as it should be) in the BIOS. 
sudo update-grub2 didn't fix it.  
Running the boot-repair tool complains "GPT detected. Please create a BIOS-Boot partition"
Parted shows that the partition is present.

---

### Post by oldfred on 2014-12-16
Boot-Repair can convert your UEFI boot of Ubuntu to BIOS boot if you add a 1 or 2MB unformatted partition with the bios_grub flag. It uninstalls grub-efi and installs grub-pc.

Post link to summary report from Boot-Repair.

UEFI is not really the issue, it is how Windows has implemented secure boot and then most vendors have made the secure boot difficult to use and restricted boot to Windows only.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by jcllings on 2014-12-16
Doesn't help though because I can see one menu and after that I get "Input not supported."   Some kind of graphics issue.  
When it rains, it pours. Now I can't get Ubuntu to boot at all or even re-install from scratch.

I can get WinBlows to boot but only if I hit it directly from the BIOS.

---

### Post by oldfred on 2014-12-16
Graphic issues almost always relater to video card/chip and what driver you have. 
I have nVidia and have to use nomodeset on live installer and on first boot or until I install the nVidia driver from the repository.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1, if not nVidia or AMD and nomodeset does not work.
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by jcllings on 2014-12-16
OK, I got the boot repair to work with nomodeset and it indicates success... but it still won't boot. :-(
I've done everything I can to disable UEFI in the Bios.

---

### Post by oldfred on 2014-12-16
Some with Samsung could only change settings in UEFI once they set a password. If your system requires that do not ever lose that password.

Post link to summary report from Boot-Repair.

       Samsung Ativ Book 9 Plus UEFI Install Troubles - manual copy of grub to /EFI/Boot
[http://ubuntuforums.org/showthread.php?t=2230919](http://ubuntuforums.org/showthread.php?t=2230919)
Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)

---

### Post by jcllings on 2015-03-20
Note to self: The problem with virtualBox turned out to be group membership in the vboxusers / vboxsf groups.

---

