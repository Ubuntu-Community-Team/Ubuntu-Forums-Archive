---
title: "i want to install ubuntu on my flashdisk"
date: 2007-08-03
forum: Dell  Ubuntu Support
---

### Post by sorgu on 2007-08-03
hey to all,

i would like to install ubuntu on my flashdisk, based on my search its possible to make it, but i cant understand the steps which i have to follow to install it.
i am using a dell notebook, i have ubuntu boot disc and 4gb flashdisk.
can somebody help me out with this?
i found this [http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/) but i cant follow it.
please keep in mind that i am not be good at computers and have been following the forum almost over a month and some of the terms and jargons you use are completely different to me. so please keep it simple english.
appreciate your time, thanks

---

### Post by sorgu on 2007-08-03
thats my hardware

DELL Inspiron 6400-C282,Core 2 Duo 1.83, X1400,Hom

Intel® 945PM Express 
Intel Core 2 Duo T5600 
1.83GHz 
667MHz 
L2 Cache 2MB  
15.4" 
Res:1280 x 800 
Picture card:ATI Mobility Radeon X1400 256 MB 
Ram:2GB (upgraded) 
DDR2 533MHz 
HD120GB 5400rpm

---

### Post by pbcartwright on 2007-08-03
what is it you don't understand? You do most of this in a terminal window, which is like the DOS command line. the command sudo means you do it as an admin, some commands require sudo in front and you put in your user password. The rest is pretty straight foward, type the commands as it says one after the other. If your results don't look like what it shows, then tell us what is confusing.
thanks

---

### Post by sorgu on 2007-08-03
> **pbcartwright said:**
> what is it you don't understand? You do most of this in a terminal window, which is like the DOS command line. the command sudo means you do it as an admin, some commands require sudo in front and you put in your user password. The rest is pretty straight foward, type the commands as it says one after the other. If your results don't look like what it shows, then tell us what is confusing.
thanks

thanks you been really helpfull.

---

### Post by ahmadzainul on 2008-05-03
[IMG]http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/[/IMG]
Requirements:

    * Ubuntu.ISO (tutorial is done from the Live CD)
    * CD Burner/Recorder
    * 1GB or larger USB flash drive

USB Ubuntu installation tutorial:

   1. Download the Ubuntu 6.10 Edgy ISO and burn it to a CD
   2. Reboot your computer into Ubuntu from the Live CD
   3. Insert a 1GB or larger USB flash drive
   4. Open a terminal window and type sudo su
   5. Type fdisk -l to list available drives/partitions. Note which device is your flash drive (example: /dev/sda) Throughout this tutorial, replace x with your flash drive letter. For example, if your flash drive is sdb, replace x with b.
   6. Type umount /dev/sdx1
   7. Type fdisk /dev/sdx
          * type p to show the existing partition and d to delete it
          * type p again to show any remaining partitions (if partitions exist, repeat the previous step)
          * type n to make a new partition
          * type p for primary partition
          * type 1 to make this the first partition
          * hit enter to use the default 1st cylinder
          * type +700M to set the partition size
          * type a to make this partition active
          * type 1 to select partition 1
          * type t to change the partition filesystem
          * type 6 to select the fat16 file system
          * type n to make another new partition
          * type p for primary partition
          * type 2 to make this the second partition
          * hit enter to use the default cylinder
          * hit enter again to use the default last cylinder
          * type w to write the new partition table
   8. Type umount /dev/sdx1 to ensure the 1st partition is unmounted
   9. Type mkfs.vfat -F 16 -n usb /dev/sdx1 to format the first partition
  10. Type umount /dev/sdx2 to ensure the 2nd partition is unmounted
  11. Type mkfs.ext2 -b 4096 -L casper-rw /dev/sdx2 to format the second partition
  12. Remove and Re-insert your flash drive
  13. Back at the terminal, type sudo apt-get install syslinux mtools
  14. Type syslinux -sf /dev/sdx1
  15. Download this custom usyslinux.tar file using the archive manager and extract the syslinux.cfg file to your "USB" stick
  16. Type cd /cdrom
  17. Type cp -rf casper disctree dists install pics pool preseed .disk isolinux/* md5sum.txt README.diskdefines ubuntu.ico casper/vmlinuz casper/initrd.gz install/mt86plus /media/usb/
  18. Reboot your computer and set your system BIOS to boot from USB-HDD or USB-ZIP. Also set the boot priority if necessary.

If everything has gone as it should, you should now be able to boot Ubuntu from the USB flash device and it should save your changes, restoring them on boot.

Notes: If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted mbr. To repair the mbr of your USB device, at the terminal type sudo apt-get install lilo then type lilo -M /dev/sdx (replacing x with the letter of your flash device)

ref. [http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/)

---

