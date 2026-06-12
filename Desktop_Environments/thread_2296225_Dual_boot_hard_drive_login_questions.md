---
title: "Dual boot hard drive login questions"
date: 2015-09-24
forum: Desktop Environments
---

### Post by A Traveller on 2015-09-24
Hi all.

On a dual boot system (both Ubuntu), whilst in drive A and wishing to access the files saved on the Desktop in drive B, clicking on the Places menu and then on drive B automatically brings up the file manager showing the files on drive B, however, whilst in Drive B and wishing to access the files on drive A, the computer's password is requested first. Why does one ask for a password and the other doesn't? Was this done during the OS installation process? Can it be changed now (after OS installation) or only during the installation process?

In either case, how can it be ensured that both disks ask for a password and how can it be ensured that both disks do not ask for a password?

On a previous occasion, on a different PC, the files saved on the Desktop on one disk could not be accessed from another disk. How is this achieved, can it be undone and also, how can this be avoided in future when installing?

Any info would be appreciated.

Thanks.

---

### Post by grahammechanical on 2015-09-24
Question #1: Did you install Ubuntu on drive A with an encrypted home folder?

As regards your second question. The files created in /home on two installs of Ubuntu on two different machines even with the same user name and password would be logged by each OS as having a different owner. Even if it was 2 installs of Ubuntu in two different partitions but with the same user name and password the ownership of folders & files created in /home would been seen as having different owners.

Something similar applies with a partition that is used as common storage for documents by more than one install of Ubuntu. Administrator/Root privileges is required to create the folder on that common partition and that sets the user of that particular install of Ubuntu as the owner of the folder. Log in to the other install of Ubuntu and as far as the folder on that common data partition is concerned you are not the owner. You may have permission to access the folder but not to create & delete files in it.

 The permissions on the folder and the files within it have to be set to allow not only access to the folder but also the authority to create & delete files for all groups & users. I believe that Linux is very sophisticated when it comes to permissions on folders and files.

Regards

---

### Post by A Traveller on 2015-09-24
Hi grahammechanical.

Thanks for your response.

I cannot remember what I did when I installed or whether I created an encrypted home folder or not. I think I did not create an encrypted folder because I can access the files from drive B. I think on the previous occasion which I have mentioned (on another PC), I had encrypted the folder and was then not able to access the files at all from another drive.

I think both current drives were set up on one machine. When trying to mount drive B from drive A, drive A asks for the password (which is the password for drive A, not drive B). Drive B does not ask for any password when mounting drive A from within drive B.

I can create and delete files in either drive from either drive.

I don't know if my reply has answered your question or not as I'm not too clear on the subject.

Would encrypting a drive (or a folder on a drive) with a third party program (veracrypt, etc) still allow the files on it to be accessed from another drive?

Thanks.

---

### Post by arminmohring on 2015-09-25
Can you post /etc/fstab?

---

### Post by A Traveller on 2015-09-29
Hi arminmohring.

FSTAB DRIVE A:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=851bc081-8b92-4d24-8f39-2aaf09b27070 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e5b0d2bb-30ee-476e-9e3d-502d4f48afcd none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


FSTAB DRIVE B:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3aa1cbbe-95a6-4283-8cf6-e5baead77633 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8edbc0ef-dbe2-4dcd-a9d8-e4f9d3d256e5 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

