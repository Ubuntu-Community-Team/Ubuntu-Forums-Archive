---
title: "Dual Boot..."
date: 2011-07-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Ath315t on 2011-07-23
I have had my antiquated Dell XPS 410 set up on a dual boot for some time now. I have no need for the highly bulky and outdated windows vista on the other side. I was wondering if there is a way to remove windows entirely from my system without harming my current Ubuntu set up. If anyone has any idea how to help or where to point me to get what I need it would be greatly appreciated.

---

### Post by GWBouge on 2011-07-24
Ideally, you should be able to boot with the LiveCD, fire up GParted, remove your Windows partition, either expand your Ubuntu partition to fill it or reformat it as ext3 or ext4, and run a 'sudo update-grub' to remove the Windows entry from Grub.  However, this depends on how your partitions are arranged, where Grub is installed, what has boot flags, etc etc.

Best method (in my opinion, at least) is to backup your /home and any important data and start fresh with the proper disk structure, just to make sure everything works as planned.  If you could post the output of 'sudo fdisk -l' (lower case L), you might get some more specialized instructions from someone with a bit more experience than I.

EDIT:  This would probably get a lot more attention in Beginner Talk or General Help as well (likely solved within an hour), since it's not really a Dell-specific request ...

---

### Post by oldfred on 2011-07-24
Welcome to the forums.

Some have second thoughts after a while. Did you make a backup of windows just in case? Do you have a vendor partition that creates DVDs that are just the image of the hard drive as purchased. Or a back up image of your current windows.

Then you can can just use gparted as posted above to remove the windows partition. You can create a new partition just for data or move /home if you do not have a separate /home. It is a bit more risky so good backups are best to move partitions around.

I think I agree with GWBouge that after good backups a new install may just be the best solution.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

---

