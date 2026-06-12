---
title: "Moving Kubuntu to a new partition (complex situation)"
date: 2006-09-07
forum: Desktop Environments
---

### Post by pielgrzym on 2006-09-07
Hello there :)

I installed Kubuntu to check how does the new KDE look and I really fell in love with it. Since I want to keep Kubuntu and don't need windows anymore (vmware is good enough) I would like to move Kubuntu to my main partition. Here is how the situtation looks:

First disk &#8211; WD 40GB &#8211; connected to mobo controller:

Primary partition:
22 GB &#8211; Windows installed + lilo installed (can't boot win any more ;) ).

Extended partition:
18 GB:
2GB SWAP
16GB XFS &#8211; here we have Kubuntu :)

Second disk &#8211; WD 160GB &#8211; connected to external PCI controller:
Two NTFS partitions, both 80GB.

Unfortunately the qtparted doesn't work on my system (it crashes after opening the NTFS 160GB disk &#8211; I installed Kubuntu with cfparted and alternate install CD). All I have now is cfdisk, and other cli tools (gparted works too, but I don't know if it won't cause trouble since it's for GNOME actually).

My plan:

1.**Delete primary partition** from wd 40GB and create:
-swap &#8211; 2GB (probably in XFS)
-boot &#8211; 100MB &#8211; in ext3 (didn't know it's important when I was installing Kubuntu)
- / - rest of space &#8211; in XFS
-mount /home on the second hard drive (size ca. 40GB)

Then:

1.Test the system for a couple of days
2.If it works delete old Linux partitions and merge them into the root partition (it's possible in XFS isn't it? How to do this?)
3.Format the rest of second hard drive and mount it as XFS &#8220;/stuff&#8221; folder

Here are my quiestions regarding the plan:

1.Can I manipulate partitions in the primary partition on the smaller disk without affecting the expanded partition?
2.How to acces the hde (smaller disk, the one I boot)? cfdisk can only see the big NTFS disk :( (called hda5 and hda6)
3.Is moving the system only a case of properly formed cp command? Please could you tell me how to exactly move the system to a new location?
4.XFS supports expanding &#8211; how to expand an xfs partition? Which command does it?
5.After succesfully reformating stuff how to install and configure grub (since now I use Lilo) to have ability to boot from old and new location (I need this temporarly to check if new system works fine)?
6.I have preload enabled &#8211; will it affect the moving of system?

Or maybe there is another way? What if I reformat the disk and install Kubuntu from scratch and then I will move the directory where installed .deb packages are located and make them install somehow? And then move home folder with all the settings? And then compile the kernel from scratch, amarok, kde, nope &#8211; I'll try to move my current system first ;)


I will be very gratefull for all your answers and suggestions :) thanks in advance :)

---

### Post by pielgrzym on 2006-09-07
Please give me at least some hints :)

---

