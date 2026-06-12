---
title: "using old home backup in separate home partition"
date: 2011-03-28
forum: Desktop Environments
---

### Post by masodin on 2011-03-28
Hi all, 

recently i made a backup of my home directory in 10.10 before reinstalling 10.10. again.
This time I chose to manually define the partitions (50GB Root, 25GB Swap, 325GB Home)

Now i wish to migrate the old home into the newly installed home, which is on a separate partition.
I have found the following documentation

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Still, as a beginner I am not quite sure about the necessary steps to perform.

As the new home is located on a separate partition is it possible to simple delete all directories there and copy all directories from old home to new home with rsync?

Do I have to install all the software that corresponds to the old home first followed by migrating home or first migrating home followed by installing the software such as thunderbird, Texlive2010 etc.

Guess that migration should take place at a later stage. Otherwise my old profile files from firefox and thunderbird will be overwriten by new ones??? 

Thanks for any help in advance,

masodin

---

### Post by Krytarik on 2011-03-28
You should do the copy process from within a LiveCD, because your own system obviously depends on the files of your home directory. And instead of deleting the fresh home directory, you should just rename it, to have a backup, just in case. Then use rsync, like you said.

Basically it doesn't matter if you first install the formerly used apps, and then restore your home directory, or if you do it the other way around. But I would prefer the latter.

In case that the profile files of the concerning apps are already in place when you launch them for the first time after their installation, those files will be used right away, and not overwritten.

Btw., why don't you just leave your home directory at the external location, and modify "fstab" instead?
See my earlier post about it: [http://ubuntuforums.org/showthread.php?p=10554669#post10554669](http://ubuntuforums.org/showthread.php?p=10554669#post10554669)

Greetings.

---

