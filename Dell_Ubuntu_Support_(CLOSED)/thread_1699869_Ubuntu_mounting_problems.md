---
title: "Ubuntu mounting problems"
date: 2011-03-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arindamC on 2011-03-04
Hi,
     I have recently upgraded from 9.04 to 10.10. There were separate  partitions for /(root) and /home. I formatted only the / partition. The  directories under the /home directory are all there, but the files are  missing. The directory hierarchy is also unchanged! 
     The corresponding device is mounted on /home. But I cannot figure  out why the files in /home are missing, even though the directory  hierarchy is preserved. Please help.


Thanks and regards,
Arindam.

---

### Post by nomko on 2011-03-04
First things first: When you do an upgrade (in your case from 9.04 to 10.10) it is bets to remove the whole partition using a live-cd of Gparted. Why? Simple: doing this avoids much trouble. 
 
Now your problem.
What happened is, and what you also confirm, you formatted the drive. And what you say that you only formatted the / partition. And now comes the clue:
 
/home is a subfolder of / (root partition).
 
So, if you format the / partition, you also clear all the subfolders and files in every other folder which is been placed in the / partition. If you want to keep your /home folder, you had to create 2 partitons on your harddrive: 1 / partition and 1 /home partition.

---

