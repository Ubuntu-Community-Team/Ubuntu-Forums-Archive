---
title: "error:  you need to load the kernel first"
date: 2011-07-16
forum: Desktop Environments
---

### Post by QuadMedic on 2011-07-16
Hi Gang, :)

Well after a power failure yesterday this is what I get:

Grub loads with 4 options ....

Choose to load Ubuntu I get ...

Error: cant load file
Error: you need to load kernel first

Guys I'm a N00b, got ubuntu 11.04 loaded on a 250 gig worked great till power failure

Can u help?

---

### Post by conradin on 2011-07-16
Boot Disk time. You probably have some corruption keeping you from booting. 
once your up and running, unmount any hard drives and start trying to repair the file systems.
Do you know the FS type?
Heres a decent link:[http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html](http://www.cyberciti.biz/tips/repairing-linux-ext2-or-ext3-file-system.html)

---

### Post by QuadMedic on 2011-07-16
Conradin, thnx m8 but I want to back-up /home first but the only way I can get close to it is with a "install CD" then use the "try" option. But I can only copy some of the files, I don't mind formating but I need to save my data in the /home folder ...
any ideas?

---

### Post by conradin on 2011-07-16
Ah good, backing up you data is a good idea!
So have you tried:
```
sudo cp -R /home /<where_you_are_BackingUpTo>
```
if that gives you errors, (Report them here)
and you may have filesytem coruption in the home directory. 
back up as much as you can.
Its not neccissary to simply reformat the drive to perform a filesystem recovery. 
Just to be clear: Did you encrypt any folders, drives, partitions or other data?

---

