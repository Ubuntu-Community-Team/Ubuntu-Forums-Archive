---
title: "my hard drives to not show on side bar of nautilus"
date: 2015-11-15
forum: Desktop Environments
---

### Post by walterramjet on 2015-11-15
i have two hard drives sda and sdb and I also have a cd/dvd drive, but none of those appear on the left side bar of Nautilus. operating system ubuntu 15.10 and nautilus 3.14.2

my etc/fstab file (I added the last line and that didn't work):
/etc/fstab: static file system information.

#
Use 'blkid' to print the universally unique identifier for a
device; this may be used with UUID= as a more robust way to name devices
that works even if disks are added and removed. See fstab(5).

#

/dev/mapper/ubuntu--vg-root / ext4 errors=remount-ro 0 1
/boot was on /dev/sda1 during installation

UUID=90e8e3dc-fdfd-4988-adc2-224b2b915674 /boot ext2 defaults 0 2
/dev/mapper/ubuntu--vg-swap_1 none swap sw 0 0

/dev/mapper/cryptswap1 none swap sw 0 0 /dev/sdb1 /hdd ext4 defaults 0 0
UUID=c12a42a2-cb9d-4712-a841-696e25e1fcbb

the result of sudo blkid:

/dev/sda1: UUID="90e8e3dc-fdfd-4988-adc2-224b2b915674" TYPE="ext2" PARTUUID="105180b1-01" /dev/sda5: UUID="opkumi-Hfh8-bdcL-qJj5-N1mj-t2bj-3jXlrL" TYPE="LVM2_member" PARTUUID="105180b1-05" /dev/sdb1: LABEL="HD2" UUID="c12a42a2-cb9d-4712-a841-696e25e1fcbb" TYPE="ext4" PARTUUID="ce9ccf02-01" /dev/mapper/ubuntu--vg-root: UUID="cf5ad1ee-5955-4aca-a7c7-f7e33f4e0693" TYPE="ext4" /dev/mapper/ubuntu--vg-swap_1: UUID="502fee58-bca7-46d1-b0e1-09d223c52f9f" TYPE="swap"
/dev/mapper/cryptswap1: UUID="e07b1b57-3e91-41bf-a222-a7dfb5ba523c" TYPE="swap"




thank you for your help,

Walter

---

### Post by grahammechanical on 2015-11-15
The CD/DVD drive will not show up until a disc is put in the drive. The partition that Ubuntu is in is usually listed as Computer. I have no experience with Logical Volume Management (LVM) or disk encryption. But those things may have something to do it.

Regards

---

### Post by CantankRus on 2015-11-16
You can hide partitions from appearing un the file browser using the installed application **disks**.
I believe this will add a line to fstab.
[**_[COLOR="#B22222"]How can I remove a HDD from the “Devices” list in the file browser?[/COLOR]_**]("http://askubuntu.com/questions/380846/how-can-i-remove-a-hdd-from-the-devices-list-in-the-file-browser/585287#585287")

---

