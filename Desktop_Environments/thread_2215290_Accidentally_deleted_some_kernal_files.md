---
title: "Accidentally deleted some kernal files"
date: 2014-04-05
forum: Desktop Environments
---

### Post by ghormley on 2014-04-05
Xubuntu 13.10 desktop .. while trying to gain space on boot partition to do daily updates, I accidently deleted the wrong kernal files.  Now Grub only shows two options and they are both memtest86 optioms.  I meant to delete all previous kermel files and did plus a bit more.  I need to reinstall the kernal using a live CD but I don't know how.  Can anyone help, please?

---

### Post by ghormley on 2014-04-05
Tried to follow the thread and command line options at
[http://ubuntuforums.org/showthread.php?t=1034523](http://ubuntuforums.org/showthread.php?t=1034523)
with no success.  It fell apart after the xhost + line.

---

### Post by deadflowr on 2014-04-06
Do you really need the xhost setting?
Shouldn't that be for running graphical apps, like synaptic, which is what caljohnsmith was looking to try.

Otherwise maybe this, easy to understand approach
[http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)
might work.

---

### Post by ghormley on 2014-04-07
Forgot to add this in original post but the problem began with a failure  of the chroot command.  

Error response was:  chroot: failed to run command '/bin/bash' : No such file or directory

Get the same error every time i perform the steps leading to the chroot command.

Thans for your assistance!

John

---

### Post by ghormley on 2014-04-08
Searching the Internet for the chroot error message led me to thisd post:

[http://forum.linuxcareer.com/threads/1618-chroot-failed-to-run-command-bin-bash-No-such-file-or-directory](http://forum.linuxcareer.com/threads/1618-chroot-failed-to-run-command-bin-bash-No-such-file-or-directory)

While I suspect there is a clue in it, it's still over my head.  

Also,  I've read that a symlink has changed in recent updates that my be the cause of this error.     I read this statement:
[I]
 /bin/bash is in the new location /usr/bin/bash (moved from /bin/bash by the
>> update) with with a proper symlink in /mnt/bin/bash pointing to ../usr/bin/bash[/I]

at this page:
[https://mailman.archlinux.org/pipermail/arch-general/2013-March/033099.html](https://mailman.archlinux.org/pipermail/arch-general/2013-March/033099.html)

While it refers to Arch, is the situation the same or similar in Debian/Ubuntu environments?

Thanks for any guidance anyone can offer.
John

---

### Post by steeldriver on 2014-04-08
Which chroot steps are you following exactly? it sounds more likely that not all the bits of your target chroot filesystem got mounted properly

---

### Post by ghormley on 2014-04-08
Thanks, steeldriver.  Here are the steps I am attempting after booting wiht a live CD (Xubuntu 13.10) and opening a terminal:

sudo mount /dev/sda1 /mnt

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys

sudo chroot /mnt

*This is where the error occurs.*

apt-get install linux-image-generic

exit
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

sudo reboot

Of course nothing else works unless the chroot works to change to the HDD as a focus for the kernal instasll.

These steps come from the page:
[http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels)

Thanks,
John

---

### Post by steeldriver on 2014-04-08
Are you 100% sure /dev/sda1 contains your Ubuntu / (root) filesystem? what is the output of 

```
sudo parted -l
```

or

```
sudo fdisk -l
```

What does

```
ls /mnt
```

say after the mount commands?

---

### Post by ghormley on 2014-04-08
**xubuntu@xubuntu:~$ sudo parted -l**
Model: ATA WDC WD10EALX-009 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   1000GB  1000GB  extended
 5      257MB   1000GB  1000GB  logical                lvm


Model: WD Elements 1023 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary  ntfs         boot


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/xubuntu-root: 997GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  997GB  997GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/xubuntu-swap_1: 3209MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  3209MB  3209MB  linux-swap(v1)

**xubuntu@xubuntu:~$ ls /mnt**
dev   etc   lost+found          memtest86+_multiboot.bin  root  tmp
dsys  grub  memtest86+.bin.jcg  proc                      sys
xubuntu@xubuntu:~$

======================

sdc was a bootable disk in another life but has never been reformatted and is not used as a bootable disk now.

Thanks,
John

---

### Post by steeldriver on 2014-04-08
OK so your root (/) is actually on a logical volume (LVM) and you have a separate /boot  - so you're going to need to 

[LIST]
[*]mount **/dev/mapper/xubuntu-root** at **/mnt** 
[*]mount **/dev/sda1** at **/mnt/boot** 
[/LIST]
 and THEN do the bind mounts I think - after which the chroot *should* find everything (famous last words...)

---

### Post by ghormley on 2014-04-09
Thanks, steeldriver!  That solved the problem and the system is booting once again with no apparent loss of data.  I certainly  do appreciate the help.  You are a lifesaver!

John

---

