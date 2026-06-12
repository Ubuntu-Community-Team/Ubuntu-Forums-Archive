---
title: "How to switch from hardware RAID 1 to RAID 5 without reinstallation?"
date: 2008-01-17
forum: Dell  Ubuntu Support
---

### Post by Zurd on 2008-01-17
It's a Dell PowerEdge with a PERC 5/i hardware RAID controller. Right now it has 2 hard disk in RAID 1 and I'd like to put 3 new drives, so a total of 5 and use this as RAID 5 without a complete format and reinstallation.

The RAID controller do support RAID 5, so that's not a problem.

Any thoughts on this would be appreciated, thanks.

---

### Post by saru411 on 2008-01-18
1st, If I'm still current on recent developements, RAID5 is not bootable via grub. I remember when trying to set this up i had much difficulty and finally came to the conclusion that RAID5 isnt bootable for me. So, you might want to install the boot sector and / in a RAID1 or RAID0 array so you can boot from that and keep the blazing speed, and then install 3-5 disks in RAID5 as your /home. This is how i set up my array and it works great

---

### Post by Zurd on 2008-01-19
Thanks, I didn't know that so I google for it a bit and found that only software raid 5 cannot handle grub and you must use the technique you described. But I have hardware raid so it shouldn't be a problem.

I was wondering if I have any option of 'RAID Level Migration' I could do which would simplify the process. Like using an application to just select RAID 5 and click on Restructure, Rebuild or something like that and it would format the 3 new drives and copy the data to make a RAID 5, that would be very nice.

As for now, one solution would be to make an image of the raid 1, then copy this image to a 3 disks raid 5, then add the 2 more hard disks and resize the partition /home from about 260G to fit the 1200G it can now support.

All 5 disks are 300G, so raid5 should be about 1200G.

---

### Post by saru411 on 2008-01-20
if you preform the installation the way you describe you should be fine. i would recommend making a /home partition. if you do make this you can easily move your files to the new arrays and not worry about reinstalling. reinstallation isnt very difficult when things go terribly wrong. you can always reinstall without formatting your /home partition.

---

### Post by dioukf on 2008-04-28
I have 2 boxes running Ubuntu 710 on RAID 5, and other 5 on RAID 1. I didn't nothing special to get it working. I think that you can't do this without reinstalling. The best way is a good backup.

---

