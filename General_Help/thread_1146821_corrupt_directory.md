---
title: "corrupt directory"
date: 2009-05-02
forum: General Help
---

### Post by nickstedman on 2009-05-02
Some directories have become corrupted. I don't know why, I just would like to get them back if possible. They are all on one partition, but it's only the directories associated with Virtualbox. The permissions have gone a bit wonky. I'm only concerned with recovering the files from one particular folder (VMshare2), but my system seems to think the folder is a character device now, and I'm not sure how to tell it otherwise...I posted this problem a few days ago, but didn't get a response. I thought I'd try asking one last time before reformatting and losing my beautiful data forever! Please help if you can.
Here's some of the output of ls -la...VMshare2 is the last entry.

---Sr-S-w-  1795 2867168839   15062318 2026646492708272234 1986-07-19 22:11 .Trash-1000
drwxrwxrwx    23 nicholas   nicholas                  4096 2008-09-30 08:50 .Trash-nicholas
?rwxrwxrwx    68      29256      12290          2684551289 1970-01-07 06:28 VBox
?r-xr-S-wT 27246 1414883941 1128674938          1718169634 2037-10-12 09:53 .VirtualBox
drwxrwxrwx     4 nicholas   nicholas                  4096 2009-05-01 18:17 vm
cr-sr-S--- 53995  448454453 2665249648             50, 133 1926-10-04 06:37 VMshare2

You can see the output of fdisk -l and mount here: [http://ubuntuforums.org/showthread.php?t=1144653](http://ubuntuforums.org/showthread.php?t=1144653)

Thanks

---

