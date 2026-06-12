---
title: "Ubuntu - resized (increased) partition size = same free space?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Robor on 2006-08-31
I had my laptop setup with WinXP Pro and Ubuntu in dual boot. Due to a failed dist-upgrade I had to reinstall Ubuntu and WinXP failed to boot anymore - no biggie as I very rarely booted Windows anyway. Well, I had 20GB of wasted space on my Windows partition so I wanted to reclaim it and use it for my root partiton (4GB of 8GB used). I did this:

1. Boot with Ubuntu LiveCD and load up GParted
2. Delete the 20 GB Windows partition (/dev/hda1)
3. Copy the '/' partition (/dev/hda2) to the former Windows partition
4. Reboot and edit the grub boot loader to boot from /dev/hda1 - boots successfully
5. Boot with Ubuntu LiveCD again and load up GParted
6. Delete the old 8 GB '/' partition (/dev/hda2)
7. Resize the /dev/hda1 partition to use the deleted partition (28 GB after resize) and reboot
8. Check the file system and it's got the same free space (4 GB) but now has 24 GB used?
9. Did a 'shutdown -F' to force a fsck on reboot - it ran but nothing changed
10. Boot with the LiveCD again and load up GParted - the newly resized partition shows 24 GB of 28 GB used 

Something doesn't make sense. If I go into 'Disks Manager' (System | Administration | Disks) it reports 'Partition 1' as /dev/hda1 with no Access Path, a size of 28.00GB (Free space not available). It reports 'Partition 2' as /dev/hda2 with an access path of '/' and the size field is blank. 

This is my fstab:
robor007@Home-T42-Ubuntu:/tmp$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda2 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 0 2
/dev/hda4 /media/hda4 ext3 defaults 0 2
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

This is the output of a 'df':
robor007@Home-T42-Ubuntu:/tmp$ df
Filesystem 1K-blocks Used Available Use% Mounted on
/dev/hda2 8260248 4101508 3822984 52% /
varrun 387084 120 386964 1% /var/run
varlock 387084 0 387084 0% /var/lock
udev 387084 148 386936 1% /dev
devshm 387084 0 387084 0% /dev/shm
lrm 387084 18316 368768 5% /lib/modules/2.6.15-26-686/volatile
/dev/hda5 46899412 26821548 18172236 60% /home
/dev/hda4 90297 4127 81353 5% /media/hda4

This is my /etc/grub/menu.lst default boot:
title Ubuntu, kernel 2.6.15-26-686
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-686 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-686
savedefault
boot

---

### Post by Robor on 2006-09-01
Bump for help - still haven't figured this out...  :confused:

I edited my fstab and changed root to /dev/hda2 to /dev/hda1.  I would think hda4 and hda5 would've moved up but they didn't. It's like it still thinks there's an hda2 there even though it was deleted with GParted (although it did error).

Here's my fstab and df output now:

Filesystem 1K-blocks Used Available Use% Mounted on
/dev/hda1 8260248 4063192 3861300 52% /
varrun 387084 120 386964 1% /var/run
varlock 387084 0 387084 0% /var/lock
udev 387084 148 386936 1% /dev
devshm 387084 0 387084 0% /dev/shm
lrm 387084 18316 368768 5% /lib/modules/2.6.15-26-686/volatile
/dev/hda5 46899412 26839396 18154388 60% /home
/dev/hda4 90297 4127 81353 5% /media/hda4

# /etc/fstab: static file system information.
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 /home ext3 defaults 0 2
/dev/hda4 /media/hda4 ext3 defaults 0 2
/dev/hda6 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

**Edit: Booting with the Ubuntu LiveCD and running GParted does not show an hda2 **

---

### Post by Robor on 2006-09-01
Solution (thanks tagra123):

sudo e2fsck -f /dev/hda1

then

sudo resize2fs -p /dev/hda1 (the -p switch isn't necessary - just gives progress)

Hope that helps someone else!

---

