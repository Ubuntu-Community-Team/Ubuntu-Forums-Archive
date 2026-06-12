---
title: "command line backup root folder"
date: 2009-04-16
forum: General Help
---

### Post by k420 on 2009-04-16
How would i back up my root folder excluding the /home, /boot, /media (i have 3 tb hdd's mounted in here).  I need a quick and simple method.  I am having issues with thte nvidia driver.  Every time i install X no longer works.  I have been trying to fix it but everytime i do i lose X.  (working on it in another post [http://ubuntuforums.org/showthread.php?p=7084784#post7084784]("http://ubuntuforums.org/showthread.php?p=7084784#post7084784")

---

### Post by codeseer on 2009-04-16
Use rsync.

---

### Post by ajgreeny on 2009-04-16
It looks more like a clone of the partition(s) that you are asking about, in which case perhaps partimage will be of use.  For straightforward backups of files, I agree rsync is the thing to use.

---

