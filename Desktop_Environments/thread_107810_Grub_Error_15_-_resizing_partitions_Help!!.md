---
title: "Grub Error 15 - resizing partitions??? Help!!"
date: 2005-12-24
forum: Desktop Environments
---

### Post by lostinpace on 2005-12-24
I currently attempted to resize the partions, w/ ubuntu 5.10 intsall cd, on my 80gig maxtor so i could use the free space to intall Ubuntu 5.10 again. Don't ask why cause idk. Well, in the process of duing this i think i resized the first partition (hdb1) to small, so consequently it wouldn't let me login into ubuntu. Now i get a grub error 15 and and can not boot up my windows os (hda1) or ubuntu os. I never did install Ubuntu a second time and don't really want to.

 I tried using a live CD to acsess my files on my linux hd, but to my surprise i find that i have 2 partitions (hdb1 and hdb5) and there is a folder that is labled "lost + found" on both partitions and there empty. i only have one file on the hardrive that i really need other wise id be willing to wipe it clean and start from scratch. Recently i booted it up with live cd and got three hardisks in disk manager: 1. /dev/hdb 2./dev/mapper/casper 3. tmpsf. I don't know, but that might have change when i tried to mount the hd while runing ubuntu 5.10 live. 

I have a 2 hardrives. 1. IDE Master-200gig Maxtor w/ windows xp 2. IDE Slave-80gig Maxtor w/ Ubuntu 5.10, my mother board is a Gigabyte (GA-7s748-L) w/ a slot A, 2500 Amd Athlon xp process, and i have 256 mb Ram.

So, if someone could tell me how to get ubuntu to boot up, or tell me how to acsess my file and back it up, that would be GREAT! :D

---

### Post by Sef on 2005-12-27
I found this on Gentoo's website about Grub Error 15:

[http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

4. Grub Error 15

Situation

This error can occur in two different stages of the GRUB configuration, either during the initial configuration (installing GRUB in the master boot record) or after booting the system and attempting to launch Linux (or any other entry). 

Code Listing 4.1: Grub Output - Initial Configuration

grub> root (hd0,0)
 Filesystem type is xfs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

Code Listing 4.2: Grub Output - Booting an Entry

Booting 'gentoo Linux'

root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel (hd0,0)/boot/kernel-2.4.20 root=/dev/hda3 vga=792

Error 15: File not found
Press any key to continue...

Solution - Initial Configuration

This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK. 

Frequently, the error notes a missing kernel image file. Make sure that the file it is referring to exists on your boot partition. 

To find out the exact name of your kernel, boot from the installation cd, mount your root and (if applicable) boot partition. Next, chroot into your Gentoo system and do a listing of the available files to see what kernel images you have available: 

Code Listing 4.3: Verifying kernel image existence

# cd /boot
# ls

This will list all the kernels that you've got on your boot partition. If your kernel is missing make sure that you compiled a kernel (using genkernel or manually): 

Code Listing 4.4: Recompile the kernel

# cd /usr/src/linux/
# make menuconfig
# make

And that you copied it to your boot partition: 

Code Listing 4.5: Copying the kernel

# cp /usr/src/linux/arch/i386/boot/bzImage /boot

Verify that the name of the kernel is exactly the same as the one mentioned in your grub.conf file. Also make sure that the kernel line in your grub.conf file is referring to that partition (either explicitly or implicitly). 

Another reported mistake is to have the BIOS ignore the disk on which the kernel or grub stages reside. Also, the partition on which grub stores its stages should not use a software RAID-5 (or other striping technology) configuration. 

Solution - Booting an Entry

First, verify that the root and setup lines you have used are correct. 

If you are certain they are valid, then you might be using a flawed GRUB version (0.93.20031222). Upgrade your Portage tree or mask this version of grub: 

Code Listing 4.6: Masking Grub

(Execute this from within the chrooted environment)
# echo "=sys-boot/grub-0.93.20031222" >> /etc/portage/package.mask
# emerge grub -p

You could also try to use the grub-install script as is recommended by the GRUB authors: 

Code Listing 4.7: Using grub-install

(The --root-directory is needed if you are using a separate boot
partition, 
 otherwise you should leave it out)
# grub-install --root-directory=/boot /dev/hda

When all this fails, your boot partition may be corrupt. Check the partition for errors: 

Code Listing 4.8: Checking a partition for errors

(Make sure the boot partition, /dev/hda1 in this case, is unmounted)
# fsck -y /dev/hda1

---

