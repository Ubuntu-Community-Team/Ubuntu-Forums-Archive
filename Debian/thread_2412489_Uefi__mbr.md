---
title: "Uefi / mbr"
date: 2019-02-13
forum: Debian
---

### Post by adam5252 on 2019-02-13
If this post if out of place, I apologize - I googled to try and find an appropriate message board to post this on and it kept coming up with this board.  If it belongs somewhere else, please let me know and I'll move it, or the mods can...

I'm at wits end with this one.  

I use rear (Relax and Recover) to do a full system, bare metal backup.  I'm using lvm to encrypt the /home partition on this system.  The partition layout looks like this:

/dev/sda1 * (boot) - type Linux
/dev/sda2 - extended
/dev/sda5 - the vg with / and /swap and /home - home is the only encrypted partition 

I can't remember if I originally installed Linux UEFI or not, but now that I have one system booting, the harddrive shows up under "Legacy" options in the boot menu.

The original system that the OS was installed a machine I put together with a Gigabyte motherboard.  I can backup/restore to another system - same make of motherboard, different harddrive with no problems.  I have several Dell Inspirons - a few 3668's and a 3670.  When I try to restore to them, they won't boot.  They go into some sort of Dell "recovery" mode and the system starts scanning the disks.  I can turn that option off in the BIOS - basically, it means that the computer can't find a way to boot from the HD.

On one of the 3668's, Windows 10 happened to be on the HD before I performed a "restore" from my USB stick -( I created a USB stick that boots rear and holds the restore image and the boot record on one USB key for ease of use. ) I was playing around in the BIOS on that system, the one that had WIndows 10 on it previously, and SOMEHOW it was able to boot in Legacy mode.  

The 3670 was unable to boot from any mode and I've tried everything.   I've tried an mbr restore by booting into a livecd and mounting the boot partition and the root partition this way...


vgchange -ay CoinScience-vg
mount  /dev/mapper/CoinSciece-vg-root /mnt/tmp
mouint /dev/sda1 /mnt/tmp/boot
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt/tmp/$i; done
chroot /mnt/
grub-install /dev/sda
update-grub

I've tried the boot repair disk - [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

and countless other things that aren't coming to mind right now and it's driving me crazy - particularly since SOMEHOW, I was able to boot off of the HD in the 3668.  

Can anyone PLEASE point me in the right direction?

Thank you in advance!  - A

---

### Post by oldfred on 2019-02-13
You would have an ESP - efi system partition (FAT32) if your install was UEFI, so it must be BIOS boot with MBR partitions since you have an extended partition.
Only with Ubuntu (not Windows) could you have gpt but boot in BIOS mode, but then would have a bios_grub partition.

But your issues with other systems are the settings in UEFI to allow legacy/BIOS/CSM boot and if from USB adapter whether you have UEFI allowing boot from USB. BIOS boot generally requires UEFI Secure Boot be off, and sometimes a separate setting for Legacy/BIOS/CSM boot.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

I do not know LVM, but a full chroot & reinstall of grub in BIOS boot mode should work. 
Also if you update UEFI/BIOS on a system that normally resets UEFI settings to defaults and you have to redo them.

      
 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by adam5252 on 2019-02-13
Thank you for your reply.  I thought the exact same thing that you suggest - chroot then reinstall mbr.  I also tried a dd if=/dev/sda of=/mnt/tmp bs=512 count=1 then turned around on the drive in question and THAT didn't work.  I'll put up a report with the Boot Repair disk.  I'm modifying my LiveUSB now to include the mbr tools (apt-get install mbr) to see if that helps.

---

### Post by oldfred on 2019-02-13
The mbr tools are for Windows booting. 
You need grub-pc for BIOS boot or if it was UEFI grub-efi-amd64.

---

### Post by adam5252 on 2019-02-14
The weirdest thing about it is that I can take the HD out of the machine that won't boot the image (Dell Inspiron 3670) and put it in a Dell Inspiron 3668 and it boots no problem.

---

### Post by oldfred on 2019-02-14
Then most often settings in UEFI/BIOS.
Did you review that settings are what you previously had. 
I have to keep a list as I change 8 or 10 settings, some required, some optional. And every UEFI update have to redo them.

Also what brand/model system?

---

