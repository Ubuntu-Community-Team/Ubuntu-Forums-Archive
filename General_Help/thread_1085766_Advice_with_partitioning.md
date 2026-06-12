---
title: "Advice with partitioning"
date: 2009-03-03
forum: General Help
---

### Post by blazemore on 2009-03-03
I have this Aspire One, and I was dualbooting Linpus and Ubuntu.

However, I now want to go pure Ubuntu.

I need some help on what partitions to delete, as I have no experience with extended partitions.

My partition setup is as follows:

---

### Post by Drate on 2009-03-03
Dang; opted out of making it easy didn't ya?

There is one thing first.  BACKUP!  PLEASE BACKUP!  After having accomplished backing up your important files (or possibly just backup your entire home directory) to an external storage device, you may proceed below or wait for other, possibly better answers.

I am going to make an educated GUESS that /dev/sda1 and /dev/sda2 are both related to Linpus and may safely be deleted.  You'll do this from either the Ubuntu side or from a LiveCD (the key point is that you can't play with a mounted partition).  From the LiveCD I believe you SHOULD be able to reintegrate the freed space into your /dev/sda3 partition by using the resize/move function in GParted.  GParted it not installed in ubuntu by default but is available on the LiveCD or with a quick look in Add/Remove Programs, or Synaptic, or sudo apt-get install gparted .

Still confused, please do not hesitate to ask for clarification.

*EDIT*  Don't forget to right click on the swap partitions and use swapoff to be able too delete the superfluous swap partition.

---

### Post by blazemore on 2009-03-03
Yeah that's the last time I let Ubuntu do its own partitioning!
I think what I'm going to do is take a complete remastersys backup of the system, back up my entire /home directory to an external hard-drive, and clean reinstall.

---

