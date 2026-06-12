---
title: "Grub menu will not appear"
date: 2018-06-27
forum: Desktop Environments
---

### Post by stickleback2 on 2018-06-27
I have a separate partition that I installed Ubuntu 18.04 onto. This partition is on one of the hard drives in my system. This is a non (EFI) system. After installation of Ubuntu, the Grub2 menu did not appear but my standard Windows 10 menu. I have tried to use "NeoSmart's EasyBsd" to aim it at the partition where Ubuntu is installed. However, after reboot and I go to the Ubuntu 18.04 entry in the menu, it throws me in the black screen grub prompt menu. I tried the ls command and I get (File system compatibility error. cannot read whole file). How can boot my Ubuntu? Thanks in advance!

---

### Post by oldfred on 2018-06-27
With multiple hard drives, did you use Something Else install option and install grub to MBR of same drive as Ubuntu. And then set BIOS to boot that drive?

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version with your live installer, not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Dennis N on 2018-06-27
> I have tried to use "NeoSmart's EasyBsd" to aim it at the partition where Ubuntu is installed. However, after reboot and I go to the Ubuntu 18.04 entry in the menu, it throws me in the black screen grub prompt menu

Common beginner mistake with BIOS is to install grub to the partition where Ubuntu is. Did you do that? You must install grub to the MBR (choose sda without the partition number for grub boot loader location if you boot to sda on startup).

---

### Post by stickleback2 on 2018-06-27
> **Dennis N said:**
> Common beginner mistake with BIOS is to install grub to the partition where Ubuntu is. Did you do that? You must install grub to the MBR (choose sda without the partition number for grub boot loader location if you boot to sda on startup).
Yes, I did.

---

### Post by stickleback2 on 2018-06-27
> **oldfred said:**
> With multiple hard drives, did you use Something Else install option and install grub to MBR of same drive as Ubuntu. And then set BIOS to boot that drive?

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version with your live installer, not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Did not set BIOS to boot that drive. Will try other links later when I get home from work. Thank you!

---

### Post by stickleback2 on 2018-06-28
Did run the Create Bootinfo summery and also learned some useful info. First of all, if you look at the enclosed image, the Linux partition (/dev/sdc5) is to the right of partition (/dev/sdc1). It is recommended that the boot should be at the beginning of the  (/dev/sdc1). Would it be possible to move this to the beginning using Gparted? Also, here is what the bootinfo had generated for me. httpp://paste.ubuntu.com/p/Qqj7TYQG28. Thanks for all of your help!

---

### Post by stickleback2 on 2018-06-28
Did run the Create Bootinfo summery and also learned some useful info. First of all, the Linux partition (/dev/sdc5) is to the right of partition (/dev/sdc1). It is recommended that the boot should be at the beginning of the  (/dev/sdc1) partition. Would it be possible to move this to the beginning using Gparted? Also, here is what the bootinfo had generated for me. [http://paste.ubuntu.com/p/Qqj7TYQG28](http://paste.ubuntu.com/p/Qqj7TYQG28). Thanks for all of your help!

---

### Post by Dennis N on 2018-06-28
> It is recommended that the boot should be at the beginning of the (/dev/sdc1) partition. 
Please clarify: What does 'boot' refer to? **bios boot** partition, or something else? My **bios boot** partition is not first on the disk and it is ok where it is. Also, I take 'beginning' to mean 'before'?

Edit:
Looked at your disk output which is msdos partitioning so bios boot does not apply there. Disregard that comment. So boot means you want a separate boot partition?

---

### Post by stickleback2 on 2018-06-28
I guess from what I got from the summary of running the Boot Repair is that (the bios boot may not be seen in the initial boot because of where it is positioned on the drive /dev/sdc5).   I'm beginning to think Dennis, that it may be better to reinstall.

[IMG]https://photos.google.com/u/1/photo/AF1QipPR-RJxpVLmfy_QPQC7KSxWYZypLRpoRAAEh0Ul?sa=X&ved=0ahUKEwjVlYigzvbbAhXn34MKHftHA0gQ9QEILDABUAE[/IMG]

---

### Post by yancek on 2018-06-28
> First of all, if you look at the enclosed image, the Linux partition (/dev/sdc5) is to the right of partition (/dev/sdc1). It is recommended that the boot should be at the beginning of the  (/dev/sdc1). Would it be possible to move this to the beginning using Gparted?

That in itself isn't a problem.  The problem might be the fact that you have a 1TB drive and you have your Ubuntu install at the very extreme end of the drive, past 94%.  Do you have a vista or other windows install on that drive or is that just data?  If you have sdc (1TB drive) set  to first boot priority it should boot.  If it doesn't, it is probably becaue it is too close to the end of the drive.  You don't need a BIOS boot partition or any boot partition.  Also, you cannot move the boot files to the beginning of the sdc1 partition because that is a windows filesystem partition.  Won't work.  You would be better off to either resize the windows partition if it is just data, move to the right from windows Disk Management or GParted.  If you don't have a lot of data in that windows partition, you could shrink it and create a Linux partition closer to the front of the drive.  If you reinstall, make sure you select to install to the MBR of the specific device (currently shown as /dev/sdc) rather than on the partition where Ubuntu is installed.  You would then of course need to set that device as first boot in the BIOS.

I would not waste time trying to boot Ubuntu from EasyBCD although it might work.  If you do want to use it, you will be better off posting any problems at the neosmart forums or a windows forum as it is windows software.

---

### Post by oldfred on 2018-06-28
Are drives set for AHCI?

Some older BIOS, must have all boot files in the first 137GB of a drive, but most of those were ones with only IDE mode. And a few newer ones in IDE mode replicate that issue. but if drive is AHCI, usually where on drive system is does not matter.

You also have nVidia and probably need nomodeset to boot until you install a proprietary driver. Since older card the open source driver may work just as well, and then you do not need to install proprietary driver.

Your sdd2 partition has issues. Looks like it may need chkdsk from Windows.

---

### Post by stickleback2 on 2018-06-28
Thanks for the great reply yancek. Yes, indeed I think being too close to the end of the drive could be the problem. This is just a data drive. Since this is a relatively new install, I think I will reinstall it side by side my Windows 10 installation on the SSD drive. Once again, thanks for the great reply!

---

### Post by stickleback2 on 2018-06-28
> **oldfred said:**
> Are drives set for AHCI?

Some older BIOS, must have all boot files in the first 137GB of a drive, but most of those were ones with only IDE mode. And a few newer ones in IDE mode replicate that issue. but if drive is AHCI, usually where on drive system is does not matter.

You also have nVidia and probably need nomodeset to boot until you install a proprietary driver. Since older card the open source driver may work just as well, and then you do not need to install proprietary driver.

Your sdd2 partition has issues. Looks like it may need chkdsk from Windows.

Yes, the drive is AHCI. And I did think I was already running the latest Nvidia driver. Will check sdd2 partition. Thank you!

---

