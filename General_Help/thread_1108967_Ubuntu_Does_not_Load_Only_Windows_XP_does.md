---
title: "Ubuntu Does not Load Only Windows XP does"
date: 2009-03-28
forum: General Help
---

### Post by abhishekswami on 2009-03-28
Hi,

I have just installed Ubuntu 8.10 Desktop Edition. I have a 200gb seagate sata hdd. I have left about 20gb for Ubuntu and the rest for windows Xp. The 20 Gb is formatted the following way:

Swap Space: 3 GB
Ext3: 16 GB

I made the ext3 FS as primary. After I finished installing Ubuntu, it asked me to remove the cd and the system restarted. Now I have a problem: 

1) I dont get a menu to choose the OS.. Only Windows Xp starts.. 

PLease let me know what I have to do to choose the OS.


PS: Windows XP was already installed on the system.

---

### Post by damis648 on 2009-03-28
It looks as though the bootloader (GRUB) didn't install properly. You can try and reinstall Ubuntu, which may work, or you can try the instructions listed [here]("http://ubuntuforums.org/showthread.php?t=224351").

---

