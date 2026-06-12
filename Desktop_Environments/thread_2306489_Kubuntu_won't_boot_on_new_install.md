---
title: "Kubuntu won't boot on new install"
date: 2015-12-16
forum: Desktop Environments
---

### Post by Telxonator on 2015-12-16
I am trying to install Kubuntu 14.04.3 x64 on a Lenovo B575 via USB. For some reason, the CD/DVD drive refuses to read DVD's, but reads CD's fine, but that's not the issue. I can get it to boot from the USB, I select install, and all goes smoothly. once it's installed, it refuses to boot, it trues the network boot, the USB, CD/DVD but refuses to boot from the HDD.

I installed it as the only OS on the computer, instructed it to use the full disk, but for some odd reason, it installs a 512 MB Fat32 partition on the HDD as the boot, then the ext2 one after that! I have never had a linux install do this, from Ubuntu, Kali, opensuse, to Fedora, and nowhere in the install did I specify this. (this happened when I tried to install Ubuntu as well.) 

I have swapped HDD's, since the original had errors with sector count, still no go.

I know it is that stupid fat32 partition, but don't know enough about changing partitions yet to edit it without some instruction. Can I delete that then expand the ext2 and add a boot flag? this is really starting to **** me off.

Thanks for any help

---

### Post by Yawanathan_Israel on 2015-12-16
Shalawam,

What is your boot order in the bios?
Are you using Bios or UEFI?
Are you partitioning the HD? or letting Kubuntu do the partitions?

As far as the DVD's go, That is probably due to the speed that the cd burner can handle? Also is the drive a dvd writer or just a reader? Most older drives are cd writers but only read DVD's

Thanks
Yawanathan

---

### Post by yancek on 2015-12-16
The FAT32 partition is most likely for UEFI so you would have to check whether you are using UEFI in the BIOS of your machine.  I believe UEFI is the default method to install on newer releases but you should be able to select whether to use it on boot.  I don't use UEFI so this is based on what I have read..  You could go to the site below and download boot repair and burn it to a CD and boot it.  When you boot, make sure you select the option to Create BootInfo Summary and do not try to make any changes.  You can post the output or a link to it here and someone will review it and make suggestions. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You don't need a boot flag set on any Linux system I am aware of,  that's strictly a windows thing.

---

### Post by Telxonator on 2015-12-16
Boot order is CD/DVD, USB, HDD, net.

No clue on UEFI, i have seen no options for it in BIOS.
And I am letting the system handle the partitions.

What is the best way to handle the UEFI? from what I hear, it is one of the dumbest designs out there.
I will try the boot CD and see what that finds

Update: the boot repair says the computer is in legacy mode, so I need to force linux to install in legacy it looks like. I'll let you know what I find

---

### Post by yancek on 2015-12-16
I don't have any UEFI computers but I would expect that you would see something in the BIOS, maybe under the Boot tab?  How old is the computer?  It's only been a few years that UEFI started being used on new computers.  If you don't resolve this, post a link to the boot repair output here and someone should be able to suggest an option for you.

---

### Post by Telxonator on 2015-12-16
fixed it by removing "EFI" folder from the install flash drive and reinstalling. Now I'm up and going! This seems to force it to install in legacy mode, as I don't believe this machine has UEFI, it was made in 2011

---

