---
title: "GRUB UEFI partition"
date: 2020-07-23
forum: Desktop Environments
---

### Post by Geoff_Lane on 2020-07-23
I have some manual entries under /etc/grub.d/40_custom for an external drive, all seems to operate correctly.  Have Mate, Debian, Raspberry Pi for PC and Arch

Now one thing is puzzling me, and that is the purpose of the EFI partition.  The reason I ask this is my BIOS is obviously set for UEFI and all my manual boot entries mount the EFI partition under /boot/efi as expected **except one, **my arch OS does not mount any EFI partition but works perfectly.

So, my question is; what is the purpose of the EFI partition?

Geoff

---

### Post by Dennis N on 2020-07-23
UEFI firmware cannot read ext4 partitions, but it can read FAT-formatted file systems. So, part of the grub bootloader files (or Windows bootloader files) are on the FAT-formatted EFI system partition. 
> my arch OS does not mount any EFI partition but works perfectly.
I don't use Arch Linux, so no idea how it works differently. But, just speculating, are there Arch Linux files on the EFI system partition? Could it unmount the partition after reading it during booting?

---

### Post by &amp;wP*!) on 2020-07-23
Arch Linux does not mount ESP to /boot/efi. Fore more information [https://wiki.archlinux.org/index.php/EFI_system_partition](https://wiki.archlinux.org/index.php/EFI_system_partition)

---

### Post by Geoff_Lane on 2020-07-31
> **pencuse said:**
> Arch Linux does not mount ESP to /boot/efi. Fore more information [https://wiki.archlinux.org/index.php/EFI_system_partition](https://wiki.archlinux.org/index.php/EFI_system_partition)

There is no ESP partition mounted at all.  If gparted is viewed there is no mount point shown for the EFI partition.

Geoff

---

### Post by oldfred on 2020-07-31
Windows does not mount ESP either.

And old versions of Windows did not mount its Boot partition. Many users did not know it was essential and saw an unknown partition, so housecleaned it out and then wondered why they could not boot.

I think the mount in fstab with Ubuntu is to know where to write major grub update. Not sure then how Arch finds ESP to update it. 
update:
I see pencuse's link explains Arch's ESP mount. They also change to use /esp, not /boot/esp.

---

### Post by VMC on 2020-07-31
As Fred said, look at Arch fstab for efi. For example here's my 
Ubuntu:
```
UUID=06F2-A932                            **/boot/efi **     vfat    umask=0077 0 2
UUID=1cc315a3-fcc9-444f-a6dd-941693e4bf66 /              ext4    defaults   0 1
```

---

### Post by Geoff_Lane on 2020-08-03
> **oldfred said:**
> Windows does not mount ESP either.

And old versions of Windows did not mount its Boot partition. Many users did not know it was essential and saw an unknown partition, so housecleaned it out and then wondered why they could not boot.

I think the mount in fstab with Ubuntu is to know where to write major grub update. Not sure then how Arch finds ESP to update it. 
update:
I see pencuse's link explains Arch's ESP mount. They also change to use /esp, not /boot/esp.

Not 100% certain here but as I boot Arch manually from entry in /etc/grub.d/40_custom I have to change the vmlinuz and initrd.img versions myself to use latest kernel.

My knowledge of GRUB (with help of this forum) has so far enabled me to recover a broken system but not fully understand what I am doing - dangerous :cool:

Geoff

---

### Post by oldfred on 2020-08-03
I believe Cavsfan uses Arch for boot, but has multiple installs and the forum thread has many posts, you may want to read first few and jump to end for latest info and work backwards.

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by Geoff_Lane on 2020-08-09
Thank you.

Geoff

---

