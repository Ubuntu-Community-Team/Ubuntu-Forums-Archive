---
title: "file system free space low"
date: 2009-04-12
forum: General Help
---

### Post by el3ntel on 2009-04-12
sorry i'm just 5 days old in linux i install ubuntu 8.10 from windows xp
i choose ntfs partition 10 gib then i have low file system free space
i use partition magic to increase space of this partition to 25 gib
i have now logical partition with huge free space but linux virtually make root.desk partition with size 5 gib and its now full how to increase the space on root.disk partition 
knowing that i install partition partition editor and disk manager and use gparted live cd and all only can see logical partition which have 18 gib free spacs
please how can i increase the size of root.disk which virtually made by ubuntu and have size of 5 gib and have no free space

---

### Post by mikewhatever on 2009-04-12
I don't think you can do it. You mist have installed Ubuntu within an ntfs partition and allocated only 5Gb to it. One way to possibly free some space is to run **sudo apt-get clean** command, which will delete all the cached updates. After that, consider reinstalling with more space available.
Edit:I may have been wrong in assuming resizing wasn't possible.
[http://ubuntuforums.org/showthread.php?t=816515](http://ubuntuforums.org/showthread.php?t=816515)

---

