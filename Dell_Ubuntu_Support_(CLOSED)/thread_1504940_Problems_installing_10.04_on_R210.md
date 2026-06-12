---
title: "Problems installing 10.04 on R210"
date: 2010-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kmdxb on 2010-06-08
Trying to install 10.04 server on a Dell R210, but it does not seem to recognise the virtual disc defined in the raid controller (RAID1 of two 500Gb SATA drives).
 
From what I can find out it is something to do with 'mpt2sas' not being present. I'm installing from the CD iso image (downloaded from [http://www.ubuntu.com/server/get-ubuntu/download](http://www.ubuntu.com/server/get-ubuntu/download) on the 4th of this month)
 
Is there an iso image I can download that does support the raid controller in the R210 (it needs to be the 32 bit server version).
 
Thanks for any help.

---

### Post by kmdxb on 2010-06-09
Found some into that might help here:
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530361](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530361)
 
[INDENT]1. Boot from the installcd
2. Go to one of the console (alt+f2)
3. Insert USB key with driver on it. (mount -t vfat /dev/sda /mnt --> or something like that)
4. Copy the required driver to /tmp (otherwise the usb i /dev/sda which is where we want the disks from the RAID card)
5. Unmount the USB key6
6. insmod the mpt2sas driver from /tmp
7. Go into the install menu and detect the disks again.
9. After install replace the generic kernel with the server kernel
[/INDENT] 
Problem is I'm not sure how to do all of the steps, in particular the last one (9)
 
Can anyone give a more details set of instructions on how to do this?

---

