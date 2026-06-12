---
title: "LVM - logical volume / disk space discrepancy"
date: 2016-12-11
forum: Debian
---

### Post by kcirtap2 on 2016-12-11
Hi there,
I am currently running Debian Jessie and I am having an issue with LVM... which I assume is going to be pretty much exactly the same as Ubuntu. I keep getting low disk space warnings for my /var partition since it is approaching 2 GB, when the logical volume is actually 15GB.
The graphical disk space analyzer shows /var partition to be only 2 GB in size, but the LVM graphical manager shows the /var logical volume to be 15 GB. I checked **/proc/mounts** and **/var** is mounted as such:
**/dev/mapper/Server--vg-var /var ext4**
**fdisk -l** reflects the same info as **/proc/mounts** and also indicates that it "should be" 15 GB.
When I run **df -h**, **/dev/mapper/Server--vg-var** size is 15 GB and used space is 1.9 GB, with 13 GB available.
And not to sound redundant, but **lvdisplay** command reflects all the same information as well.

Just in case, I ran these commands again in the unlikely event the logical group wasn't "resized" from my live Debian bootable USB I made:
**e2fsck -f /dev/Server-vg/var**
**resize2fs /dev/Server-vg/var**
but it said **The file system is already 3932160 (4k) blocks longs. Nothing to do! **&#8203;~15GB

So I'm curious if anyone might know how to make the disk space reflect the logical volume space I have allocated for it?
Thank you in advance for any info or insight.

---

### Post by deadflowr on 2016-12-11
*Thread moved to **Debian**.*

---

### Post by TheFu on 2016-12-12
df -i?

---

### Post by kcirtap2 on 2016-12-14
Sorry for the slow reply, I'm just in the middle of final exams right now.
Here is the result of **df -i** for /var

**/dev/mapper/Server--vg-var      956160  54294     901866    6% /var**

---

