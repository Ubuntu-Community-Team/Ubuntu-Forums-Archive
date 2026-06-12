---
title: "how to remove ubuntu"
date: 2005-04-25
forum: Desktop Environments
---

### Post by vedo071 on 2005-04-25
sory if i this question was posted before, but can anyone tell me what's the easyest way to remove ubuntu.I have win xp on first partition, ubuntu on second and third partition which I use just for music and stuff. I now want to instal slack instead. when i boot my slack cd cfdisk cant see my partitions. Is there any way to format that partition and remove GRUB from my mbr, without having to boot win xp cd and doing fixboot or fixmbr.

I hope someone will understand what I want to do.  :-)  :-)  

and one more thing, it's SATA drive.

thanks

---

### Post by nad on 2005-04-25
If slack can't see your partitions, may I suggest that you search their forums for the information that you require?

To remove ubuntu, just delete all files. If your exPee install recognizes the partitions, you should be able to modify your drive from there. To repair your mbr you need to use somebody's software unless you know how to access and manipulate that first sector yourself.

---

### Post by Mat10 on 2005-04-27
Use your XP startup or emerg disk  at prompt use > fdisk/MBR

I've had to do this several times in the past cleaning up the boot record so I can install a different distro.  Note that mine has always been for a Linux partition only.
The tool is good and works better than partiton magic 8 when grub is left on the MBR.   If you can get a copy of partition magic it is a good tool also to have on hand.  It takes more than one simple single tool sometimes to mix and move these systems.   If you have a ME start disk the command is the same.


Tom

---

