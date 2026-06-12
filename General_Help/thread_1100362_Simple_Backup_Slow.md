---
title: "Simple Backup Slow"
date: 2009-03-19
forum: General Help
---

### Post by _2009 on 2009-03-19
Hi,

I just got our first Linux server up and running using Intrepid, so far I'm very happy with the choice of OS.

I'm now setting up our backup strategy for the data on the new server and I'm finding it 

Prior to this I backed up our old server across the gigabit LAN to a removable SATA drive in my XP 64 workstation. To backup around 400GB used to take about 12 hours. Which was slow but acceptable.

Now with the new server I thought I could speed this up by installing the removable disk into the server, so the data is all transferred locally from the Raid 5 data array to the removable SATA disk. But it's been going 22 hours and it's not finished yet!

Here's a bit more info:
1.The array and the removable drive are on the same "on board" SATA II controller.

2.The data array is software raid 5 ext3, the removable disk is NTFS.

3. The server was setup using LVM.

Any ideas?

Thanks in advance for your help,
_2009

---

