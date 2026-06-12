---
title: "Partitioning issues"
date: 2005-12-08
forum: General Help
---

### Post by faisalK on 2005-12-08
I already have the dual boot system setup. But I want ot make more space for a fat 32 partition. to share with windows. 
I tried edit the partition table using the intallation partitioner. but every time I told it to partition it would do nothing. It would just go back to the screen without partitioning

Then I installed ubuntu on another hard disk and downloaded Gparted and connected my dual boot hard disk via USB ide. and the same thing happened with Gparted. I set the changes and when I pressed apply it just went back to the screen with the partitions as they were. 

It does just does not want ot partition it. I cannot use parititon magic in windows cause it messes up the Grub loader. 

Any ideas

---

### Post by codejunkie on 2005-12-08
[quote=faisalK]I already have the dual boot system setup. But I want ot make more space for a fat 32 partition. to share with windows. 
I tried edit the partition table using the intallation partitioner. but every time I told it to partition it would do nothing. It would just go back to the screen without partitioning

Then I installed ubuntu on another hard disk and downloaded Gparted and connected my dual boot hard disk via USB ide. and the same thing happened with Gparted. I set the changes and when I pressed apply it just went back to the screen with the partitions as they were. 

It does just does not want ot partition it. I cannot use parititon magic in windows cause it messes up the Grub loader. 

Any ideas[/quote] you could try using partition magic to resize the partition, and then use your ubuntu install cd to reinstall grub if it gets messed up by using partition magic heres a guide to help you with repairing grub [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation]("http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation")
Edit: and probably the reason your having troubles partitioning that drive with gparted and the ubuntu installer is, if it's using ntfs neither support the ntfs file system right now.

---

