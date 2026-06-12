---
title: "Can I run Ubuntu Netbook Remix from Flash Drive?"
date: 2008-11-03
forum: Desktop Environments
---

### Post by markw10 on 2008-11-03
I currently have an MSI Wind running Mandriva PowerPack 2009. I want to try Ubuntu Netbook Remix.  If I'm correct it's out already but there is either a cost for it or the availability is limited.  
I want to try it though and maybe even use it regularly. 
My question is I don't want to get a 2nd notebook but will it be possible to get something like an 8GB flash drive and just plug that into my Wind and then choose to boot from Flash Drive whenever I want to run it?

---

### Post by Blackwolf_Oz on 2008-11-03
Try just doing this. Ubuntu 8.10 Persistent flash drive install using the Live CD. This tutorial will enable a user to install Ubuntu 8.10 Intrepid Ibex to a USB flash drive while booted from the Live CD. In addition the persistence or casper persistent feature will be utilized to automatically save changes back to the thumb drive as you work, and then restore those saved changes upon subsequent boots.


Note: A very nice USB Installer is now included on the Ubuntu 8.10 CD, Please use this > USB Ubuntu 8.10 Flash drive installer instead!
Ubuntu 8.10 USB installation essentials

    * Working CD Drive and an Ubuntu 8.10 CD
    * Established internet connection
    * 1GB or larger USB flash drive (2GB or larger for script installations)

Create Ubuntu 8.10 flash drive automatically

Note: With this method, you must use a 2GB or larger thumb drive.

   1. Download the Ubuntu 8.10 ISO and burn it to a CD
   2. Restart your computer, booting from the Live CD
   3. Insert a 2GB or larger USB flash drive
   4. Open a terminal and type the following into the terminal window:

          wget pendrivelinux.com/downloads/u810/u810.sh

          chmod +x u810.sh && sh u810.sh

   5. Follow the onscreen instructions
   6. Once the script has finished, reboot your computer and set your BIOS or boot menu to boot from the USB device

Create Ubuntu 8.10 flash drive manually

   1. Download the Ubuntu 8.10 ISO and burn it to a CD
   2. Restart your computer and boot from the Ubuntu Live CD
   3. Insert a 1GB or larger USB flash drive
   4. Open a terminal window and type sudo su
   5. Now type fdisk -l to list available drives/partitions (note which device is your flash drive Example: /dev/sdb). Throughout this tutorial, replace all instances of x with your flash drive letter. For example, if your flash drive is sdb, replace x with b.
   6. Type umount /dev/sdx1
   7. Type fdisk /dev/sdx
          * type p to show the existing partition and d to delete it
          * type p again to show any remaining partitions (if partitions exist, repeat the previous step)
          * type n to make a new partition
          * type p for primary partition
                o type 1 to make this the first partition
                o hit enter to use the default 1st cylinder
                o type +750M to set the partition size
                o type a to make this partition active
                o type 1 to select partition 1
                o type t to change the partition filesystem
                o type 6 to select the fat16 file system
          * type n to make another new partition
          * type p for primary partition
                o type 2 to make this the second partition
                o hit enter to use the default cylinder
                o hit enter again to use the default last cylinder
                o type w to write the new partition table
   8. Type umount /dev/sdx1 to unmount the partition
   9. Type mkfs.vfat -F 16 -n ubuntu810 /dev/sdx1 to format the first partition
  10. Type umount /dev/sdx2 to ensure the partition is unmounted
  11. Type mkfs.ext2 -b 4096 -L casper-rw /dev/sdx2 to format the second partition
  12. Remove and re-insert your flash drive (if prompted that a new medium has been detected, select to open in a new window and click ok)
  13. Back at the terminal, type sudo apt-get install syslinux mtools
  14. Type syslinux -sf /dev/sdx1
  15. Type cd /cdrom
  16. Type cp -rfv casper dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines install/mt86plus /media/ubuntu810
  17. Type cd /media/ubuntu810
  18. Type cp isolinux.cfg syslinux.cfg
  19. Type rm text.cfg
  20. Type wget pendrivelinux.com/downloads/u810/text.cfg
  21. Reboot your computer and set your system BIOS boot priority to boot from the USB stick

---

