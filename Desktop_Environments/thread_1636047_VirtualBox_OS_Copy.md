---
title: "VirtualBox OS Copy"
date: 2010-12-02
forum: Desktop Environments
---

### Post by Albundy213 on 2010-12-02
im running Ubuntu 10.04 and just installed the most recent virtual box. I installed XP as one of the OS but its acting up now. I will reinstall a new copy of XP but how can i make a copy of my XP so i can have it as a backup just in case. 

Thanks

---

### Post by Liverbones on 2010-12-02
You can make a copy of the virtual hard drive image, which would essentially function as a complete OS backup. You'll have to open up a terminal and type [FONT="Monospace"]VBoxManage clonehd <filename> <newfilename>[/FONT], where <filename> is the name of the hard disk you want to clone, and <newfilename> is what you wish to call the copy. You should then be able to load that copy into a virtual machine without headaches.

Hope that helps. :)

---

