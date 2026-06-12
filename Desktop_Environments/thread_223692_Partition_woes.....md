---
title: "Partition woes...."
date: 2006-07-26
forum: Desktop Environments
---

### Post by CrimsonTider12 on 2006-07-26
First off, let me just say that I recently installed Ubuntu, and I love it!

My computer has two hard drives, a 40 GB with Windows XP, and a 60 GB with Ubuntu.  I have run out of space on the Windows hard drive, and would like to set up a partition on the 60 GB hard drive for some Windows files/programs.  I have tried doing this on two seperate occassions with PartitionMagic 8.1 in Windows, but both times it screwed up my system and I had to spend a day fixing it.  While I love to try doing stuff like this on my own, I think I may need some help on this one.  What is the best way for me to set up this partition and have both Ubuntu and Windows still boot?  Thanks in advance ;)

---

### Post by NobodySpecial on 2006-07-26
Correct, do NOT use Partition Tragic to resize an ext filesystem.

Get the Ubuntu Dapper install CD (Live CD) and boot to it.  Run the GPARTED program.  Resize the last partition on your hard drive.  Then create a new FAT32 partition.

---

