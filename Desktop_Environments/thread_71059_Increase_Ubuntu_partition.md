---
title: "Increase Ubuntu partition"
date: 2005-10-02
forum: Desktop Environments
---

### Post by peterthebike on 2005-10-02
I used to have a dual-boot system but now I no longer need the Windows XP.
I deleted the /dev/hda partition, but now I cannot resize /dev/hd3. QTparted, parted and gparted all seem to not allow moving the start of the partition.
Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Device Boot      Start         End      Blocks   Id  System
/dev/hda2            2386        2482      779152+  82  Linux swap / Solaris
/dev/hda3             654        2385    13912290   83  Linux
Following other postings I have also tried using the installation CD and running the manual partitioning, but I could not find a way of resizing /dev/hd3 there.
The only option seems to be completely re-installing!!
Any suggestions would be most grateful.
Peter

---

### Post by jrib on 2005-10-02
This isn't the answer to your question exactly but it is a suggestion:

I just did a similar thing.  I wanted to make my Ubuntu partition larger with some extra space I had on my drive.  I was unable to do it as well but someone suggested that I make a new partition for /home.  There is a HowTo [here]("http://ubuntuforums.org/showthread.php?t=46866") and it is apparently good practice to have /home on a seperate partition.  Hope that was somewhat helpful.

---

