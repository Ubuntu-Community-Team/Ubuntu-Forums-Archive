---
title: "NTFS External Harddrive"
date: 2006-02-07
forum: Desktop Environments
---

### Post by rohan! on 2006-02-07
Hi,
I'm currently making the move over to Linux from winxp, I have two questions one major and the other not so...

1// I have an external harddrive (format:: NTFS, size:: 250gig) with over 70gigs of data on it. I want to change this to FAT so that I can use it with different OS's, but don't want to loose all the data already on it. Is there anyway (short of having to transfer the contents of the drive to another computer) to deal with this?? Is it possible to partition the drive in half, format one half to FAT and then just transfer the contents of the other half to that side, without losing data?? Is this just a dream??

2// I am partitioning my laptop's harddrive, and am going to have it dual boot with Ubuntu linux on one partition and Arch linux on the other. If I install programs to Ubuntu will I be able to use them in Arch or do I have to install again??

Cheers

---

### Post by frodon on 2006-02-07
1/ Yes the best solution woud be to create a FAT32 partition with unused space then transfert your datas on it, after that convert the 70Go NTFS partition to FAT32 and after that if you wish  ... merge the 2 partitions to get a 250Go FAT32 partition.

---

### Post by FrankTM on 2006-02-07
[QUOTE=rohan!]Hi,
I'm currently making the move over to Linux from winxp, I have two questions one major and the other not so...

1// I have an external harddrive (format:: NTFS, size:: 250gig) with over 70gigs of data on it. I want to change this to FAT so that I can use it with different OS's, but don't want to loose all the data already on it. Is there anyway (short of having to transfer the contents of the drive to another computer) to deal with this?? Is it possible to partition the drive in half, format one half to FAT and then just transfer the contents of the other half to that side, without losing data?? Is this just a dream??

2// I am partitioning my laptop's harddrive, and am going to have it dual boot with Ubuntu linux on one partition and Arch linux on the other. If I install programs to Ubuntu will I be able to use them in Arch or do I have to install again??

Cheers[/QUOTE]

keep in mind that if this data is really important to you, you _REALLY_ should consider making backups
you wouldn't be the first to loose data on partitioning

---

### Post by rohan! on 2006-02-07
[QUOTE=frodon]1/ Yes the best solution woud be to create a FAT32 partition with unused space then transfert your datas on it, after that convert the 70Go NTFS partition to FAT32 and after that if you wish  ... merge the 2 partitions to get a 250Go FAT32 partition.[/QUOTE]

Sounds good... but how do i do it??

---

### Post by StefanoCole on 2006-02-07
You can install GParted to do it. It is a grafical tool to partition. It is similar to the commercial partitioning tool "Partition Magic".

Stefano

---

