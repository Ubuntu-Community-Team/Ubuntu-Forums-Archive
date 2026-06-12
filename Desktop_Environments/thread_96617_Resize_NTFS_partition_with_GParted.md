---
title: "Resize NTFS partition with GParted"
date: 2005-11-29
forum: Desktop Environments
---

### Post by StefanoCole on 2005-11-29
Hello, I have noticed that the live CD has the application GParted. I would like to know if someone has used it to resize a NTFS partition with Windows XP installed. Of course, before attempting it on my PC I would backup everything, but I wanted to know if, in general, it is a feasible operation.

Thank you, Stefano

---

### Post by kwaanens on 2005-11-29
Gparted does not do this, as far as I know. However, qtparted does. Try using sysresccd.org. Boot with the CD and resize at will. (I have never actually backed up the system before using it, but of course it is always smart).

Remember: defrag your Windoze-partition before resizing it, just to be on the safe side!

- Ketil

PS. QT can resize NTFS. However, Gparted can copy partitions. That proved to be invaluable to me at one point, so I had to reboot several times, using first one (sysresccd), then the other (ubuntu live). Hopefully either one will introduce what it doesn't already have.

---

### Post by kalin on 2005-11-29
Actually GParted *can* resize NTFS partitions, as long as the "ntfsprogs" package is installed. On the live CD I think it's not, but if you manage to get it online you can "sudo apt-get ntfsprogs" (or simply use synaptic). I haven't tried it personally.

---

### Post by kwaanens on 2005-11-29
You're quite right! I checked on my computer. However, resizing of ntfs partitions is mainly needed before installing Ubuntu, so it should be packaged with Ubuntu Live! In the spririt of user autonomy :)

- Ketil

---

### Post by kalin on 2005-11-29
Correction: just booted a live cd to see what's on it, and I was wrong, it comes with ntfsprogs, and GParted supports the NTFS operations running off it.

---

### Post by Chuckaluphagus on 2005-11-29
I've done a resize of an NTFS partition using qtparted, it should work exactly the same with Gparted I believe.  Everything went flawlessly for me, but I did take these precautions first:

1: Defrag the NTFS partition.  Possibly do it several times; you want loose data cleared off the end of the partition that you're going to be shrinking.

2: For the love of all you hold dear, back up the NTFS partition.  Unless it's a bare Windows install with nothing set up, don't muck around with partitioning without having a backup handy.

Good luck, post if you run into problems.

---

