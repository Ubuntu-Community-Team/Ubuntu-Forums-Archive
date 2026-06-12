---
title: "IDE 2*HDD RAID help."
date: 2006-01-25
forum: Desktop Environments
---

### Post by chris_andrew on 2006-01-25
Hi,

I'd like to set-up (software) RAID on a spare box at home.  I have two spare HDD's of similar size, and would ideally like the following partitions:

/boot
/
/home

Does anybody know of a good guide that could help me.  I have acheived this using Opensuse, but they use an installer which makes this pretty trivial.

Any help appreciated.

Many thanks,

Chris.

---

### Post by lha on 2006-01-26
[QUOTE=chris_andrew]Hi,

I'd like to set-up (software) RAID on a spare box at home.  I have two spare HDD's of similar size, and would ideally like the following partitions:

/boot
/
/home

Does anybody know of a good guide that could help me.  I have acheived this using Opensuse, but they use an installer which makes this pretty trivial.

Any help appreciated.

Many thanks,

Chris.[/QUOTE]

I have software raid1 and it was very easy to set up. First, partition your hard drives with identical partitions. (They don't really have to be identical, but it's simpler and wont waste space if they are.) I prefer cfdisk, but installers partitioner will do fine, too. Then select create md devices. Select raid level and partitions you want to have on that md device. Md devices will appear in the partitioner. Give them mount points and select filesystems. Continue install as usual. Grub is installed only to one drive and if you want to have grub on the other hd, too, see [here]("http://deb.riseup.net/storage/software-raid/").

Remember: Grub can't boot from raid0, only from raid1. So atleast boot has to on raid1 if raided at all. I also remember reading that root on raid!=raid1 may cause some issues, but I'm not 100% certain on this. If you have any further questions, I'll try to answer. As you have no data to lose on your computer, just try to do it. It isn't much different from a regular manual partitioning.

---

### Post by chris_andrew on 2006-01-27
lha,

Thanks for your advice, i'll have a look at what yo've said, and post my results.

Thanks, again.

Chris.

---

