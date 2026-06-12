---
title: "America's Army permissions"
date: 2005-08-26
forum: Gaming &amp; Leisure
---

### Post by agds on 2005-08-26
I can't run America's Army.  I had to install it to a FAT32 partition I share with Windows due to insufficient space on my Linux partition.  I don't see why this should make a difference, but this doesn't seem to be a (well-)documented problem.  When I click the launcher, I get the following message.> **Cannot launch entry**

Details: Failed to execute child process "/media/windows/armyops//armyops" (Permission denied)I've tried "sudo chmod +x" and "sudo chmod a+rx" with the executable and the shell script to no avail.  I don't understand permissions as well as I should, so it's entirely possible I'm missing something obvious here.  Your help would be much appreciated.

---

### Post by arnieboy on 2005-08-27
[QUOTE=agds]I can't run America's Army.  I had to install it to a FAT32 partition I share with Windows due to insufficient space on my Linux partition.  I don't see why this should make a difference, but this doesn't seem to be a (well-)documented problem.  When I click the launcher, I get the following message.I've tried "sudo chmod +x" and "sudo chmod a+rx" with the executable and the shell script to no avail.  I don't understand permissions as well as I should, so it's entirely possible I'm missing something obvious here.  Your help would be much appreciated.[/QUOTE]
u have to check whether u have execute permissions on the FAT32 permission or not.
check ur /etc/fstab file to make sure u have umask=000 for the FAT 32 partition. if thats fine, try playing the game with "sudo /location_of_file/armyops" where u have to obviously put in the correct path.

---

### Post by agds on 2005-08-28
I checked my /etc/fstab and I have umask=000 for that partition.  I also tried using sudo as you suggested.  It returned a similar "Permission denied" message.

---

