---
title: "add more space to wubi installation?"
date: 2009-02-08
forum: General Help
---

### Post by Sarai the Geek on 2009-02-08
I installed ubuntu through wubi because my computer was having problems creating partitions. I allocated something like 30GB to the install, haven't used a lot of it but considering that I use the Ubuntu like 90% of the time and Windows only 10% but there's like 100GB left to Windows, is there a way to adjust the amount of space allocated to ubuntu?

---

### Post by Orlsend on 2009-02-09
**From the Wubi guide**


"How do I resize the virtual disks?

You can use LVPM, at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

As an alternative, you can use the following script to move /home or /usr to a dedicated virtual disk.

Download wubi-add-virtual-disk, open a terminal and run:

sudo sh wubi-add-virtual-disk /home 15000

Where the first argument is the directory to move to a new dedicated disk, and the second argument is the size in MB.

The 2 directories you are most likely to migrate are /home (if you have a lot of user data) and /usr (if you installed a lot of software).

You should now reboot. If you are happy with the result, you can now remove /home.backup. To undo the changes remove /home, copy rename /home.backup to /home and remove the /home line in /etc/fstab.

How do I create a virtual disk in Ubuntu?

Open a terminal (Applications -> Accessories -> Teminal), and enter these commands (this will create a 10 GB extra.virtual.disk, adjust line 2 to change these):

cd /host/ubuntu/disks
sudo dd if=/dev/zero of=extra.disk bs=1MB count=1 seek=10000
sudo mkfs.ext3 -F extra.disk

How do I create a virtual disk in Windows?

You can use qemu-img for that. Another dirty trick (but working) is to copy any other file of the desired size to c:\wubi\disks and rename it "root.disk", "home.disk", "swap.disk" or "extra.disk". That's the wubi equivalent of buying (and installing) a new hard disk ;)

If you are running Windows XP (may work in Windows 2000 and Vista as well) you can create a file by using the fsutil that is included with Windows. The command format is fsutil file createnew filename filesize where filename is the file you wish to create and filesize is the size of the file to be created in bytes."

**You could resize your current isntallation or make a new virtual drive.**

---

