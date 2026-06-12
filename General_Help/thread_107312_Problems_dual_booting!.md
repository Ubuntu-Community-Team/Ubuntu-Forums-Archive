---
title: "Problems dual booting!"
date: 2005-12-22
forum: General Help
---

### Post by hexedecimal99 on 2005-12-22
Maybe someone can help me out with this if I explain the process I went through to install ubuntu-

1. I had windows xp, and i used partition magic to make a 7 gig partition for ubuntu, and a 500 mb swap partition
2. Partition magic did its work and rebooted, I immediately installed Kubuntu on the 7 gig partition and used the 500 mb partition for swap. The installation was sucessful and i was able to run kubuntu.
3. I rebooted my computer and selected windows xp from the boot manager, i guess some how it was wiped out during the installation, i got an error message at the login s
4. I rebooted again and reinstalled windows xp, it recognized the 2 linux partitions and the xp partition, i reinstalled over the xp partition.
5. Windows is now up and running but their is no boot manager when i start up so it automatically goes to windows. I know i didnt install over linux because when i check C:\'s properties in windows, it says the total capacity is 67 GB so something has to be taking up the extra space (its an 80 gig HD)

Any ideas on how to get the boot manager back? (preferably a safe way, my family is getting mad at me because its the 2nd time ive wiped out windows in a week from different causes lol ;) )

---

### Post by darth_vector on 2005-12-22
it sounds like windows has overwritten the master boot record. this contains - in most cases - the first parts of grub. you will have to reinstall grub. this isnt a difficult process and there are heaps of posts and howto's on how to do it.

---

### Post by darth_vector on 2005-12-22
look at:

[http://ubuntuforums.org/showthread.php?t=76652&highlight=reinstall+grub+howto](http://ubuntuforums.org/showthread.php?t=76652&highlight=reinstall+grub+howto)

---

### Post by Sutekh on 2005-12-22
[Ubuntu Forum - Restoring GRUB]("http://ubuntuforums.org/showthread.php?t=24113")

[Ubuntu Wiki - Recovering GRUB]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")

---

### Post by hexedecimal99 on 2005-12-22
Thanks a lot for the fast replies! Ubuntu is back up and running.

---

