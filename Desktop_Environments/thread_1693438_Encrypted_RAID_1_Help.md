---
title: "Encrypted RAID 1 Help"
date: 2011-02-22
forum: Desktop Environments
---

### Post by _joecrawford on 2011-02-22
Okay - I am not sure how to pose this question and sound intelligent, but I will put it out there.  

1-  I want to encrypt my system drive
2 - I want to make my system drive a RAID 1
3 - I have two 1 T hard drives, but I would like to be able to add two more 1 T hard drives for a total of 4 1T drives in the future.  How do I do that?

I am using ubuntu 10, desktop edition.  I have not added the OS yet, I am building this weekend. Thanks!

---

### Post by deconstrained on 2011-02-22
> **_joecrawford said:**
> How do I do that?
Read a wiki article.

No, seriously, it's how I did it. It's definitely not an insurmountable challenge.

The general steps to doing it are
1. Boot to livedisk
2. Install the necessary utilities (and [kill mdadm!](http://ubuntuforums.org/showpost.php?p=10477744&postcount=4))
3. Partition disks
4. Create mdadm array(s) from disk partitions
5. Assemble RAID(s) 
6. luksFormat the mdadm device(s) and start them
7. Make filesystem(s) on the luks device(s)
8. Install Ubuntu using the 'select partitions manually'
9. Mount the filesystems & chroot
10. Configure your system (/etc/fstab, /etc/mdadm/mdadm.conf, /etc/crypttab, /etc/initramfs-tools/modules) and install missing software (mdadm, cryptsetup)
11. Rebuild the initramfs
12. run grub-update and install GRUB on one (or more if you please) of your drives
13. Exit chroot, unmount everything, cross your fingers and reboot.

I found the ArchWiki articles on Software RAID/LVM and luks for dm-crypt particularly helpful. To be honest though, it took a few attempts at first. The place where you're most likely to mess up is forgetting to add something in your system configuration that gets parsed by update-initramfs (thus making a Linux image that won't boot). By the time you're done you'll probably have the procedure for rebuilding your initramfs memorized ;-)

---

### Post by deconstrained on 2011-03-05
Hey one more thing: I migrated recently from RAID 5 to 10 when I got a fourth drive (WAY faster than 5, I highly recommend). My non-encrypted boot partition is a RAID 1, and in the process, I learned how to grow it:

mdadm --add /dev/md0 /dev/sda1

That will add it as a spare. You then need to "grow" the array to use all four partitions:

mdadm --grow /dev/md0 --raid-devices=4

Good luck!

---

