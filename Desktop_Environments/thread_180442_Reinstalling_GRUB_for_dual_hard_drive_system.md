---
title: "Reinstalling GRUB for dual hard drive system"
date: 2006-05-22
forum: Desktop Environments
---

### Post by jccj7 on 2006-05-22
After conducting a search and gathering the major steps, I still need some detailed guidance to ensure I don’t mess this up.  I figured this is one of those “measure twice and cut once” situations.

Anyways – before re-installing WinXP Pro on my master hard drive, I had a slaved, second hard drive where Ubuntu resided.  I swapped between systems via GRUB during boot.

I just reinstalled WinXP (on the master hard drive) and understand that GRUB needs to be reinstalled via Live or the installation CD to regain access to Ubuntu residing on the slaved drive.  I have the major steps, but need some refined help on correctly choosing my drives and partitions.  I’m using the [wiki]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28recoveringubuntu%29") instructions 

The issues:

1.	Do I preserve the Windows bootloader?  I’m thinking ‘no’, which means I will overwrite the bootloader, correct?  

2.	Where do I install GRUB??  Do I install it on the master drive (WinXP), the slaved drive (Ubuntu), and which partition?  Based on the RESCUE command via the installation disc, here is my drive and partition array”

Dev/discs/disc0/part1
Dev/discs/disc0/part2
Dev/discs/disc0/part5
Dev/discs/disc1/part1
Dev/discs/disc1/part2
Dev/discs/disc1/part5

3.	More facts - My master drive does have 2 partitions (C and D).  I thought when I installed Ubuntu on the slave, it was under one partition, but based on the above report – not sure now.

Need some help on cracking the hard drive and partition code!!!!  Beggars can't be choosers - but some help on the Terminal commands would help.

Thanks

jc

---

### Post by jccj7 on 2006-05-23
OK, I guess I cried Uncle too early and dug through some discussions via refined searches.

I used several comments from these posts 

[#1]("http://www.ubuntuforums.org/showthread.php?t=24113&highlight=restore+grub") 

[#2]("http://www.ubuntuforums.org/showthread.php?t=76652&highlight=restore+grub")

Thanks to vnbuddy2002 for the steps and Curlydave for refining them for inexperienced users. 

Here is the exec summary that worked for me:

1. Boot your computer up with Ubunto Install CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Select your appropriate Linux partition using the up and down arrow keys, and press enter. Then select the "mount point" option, and press enter. From the list, select the "/" option that indicates the root file system. Select the option labled "bootable flag" by pressing enter on it. Save the changes to the partition.
5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Super easy and only took 5 minutes.  The key is the additional info Curlydave added in step 4 that will get you through the confusing areas.

Enjoy,

jc

---

