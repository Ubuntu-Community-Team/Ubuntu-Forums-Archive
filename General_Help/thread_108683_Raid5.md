---
title: "Raid5"
date: 2005-12-26
forum: General Help
---

### Post by ttallos on 2005-12-26
Hi I was wanting to set up a kubuntu box with raid 5. Just a simple setup I have 3 Hard Drives 1 is 41Gig and the other 2 are 40 I was having a problem getting the boot loader to work after making dev/md0. I really don't know how to partition for RAID5. I want the OS on the Array. I know I can do this and make it work with enough headbanging! My question is there anyone out there who knows how to partition each drive and then the array to get Breezy 5.10 to load the bootloader? Sorry if I am not giving enough info I have worked on this for 4 hours now.

---

### Post by ttallos on 2005-12-26
:KS More info on my post I have 3 master Drives with a basic promice ATA 66 IDE Controller No RAID Card. I want the software to do all the work. I am new to this. I am loading now and think this config will work for now.

Drive 1 hda (master)
Partition info     #1 Primary  2.7 GB Active Ext3
                      #5 Logical 1.5GB  swap
                      #6 37GB RAID
Drive 2 hdc
Partition info      #1 primary 37GB RAID
                        3.1GB Free
Drive 3 hde
Partition info      #1 primary 37GB RAID
                        3.1GB Free

---

