---
title: "gedit: Could not create a backup file while saving"
date: 2009-05-11
forum: Desktop Environments
---

### Post by 55tptag on 2009-05-11
Description of problem:
Opening a file with gedit, editing the file and trying to save by ^S.
But then getting an error message:
---------------------------------------------------------------------------
Could not create a temporary backup file while saving <my file>

gedit could not backup the old copy of the file before saving the new one. You
can ignore this warning and save the file anyway, but if an error occurs while
saving, you could lose the old copy of the file. Save anyway?
---------------------------------------------------------------------------
By clicking "Save Anyway" I can temporarily rid the problem. 

The problem persists since Ubuntu 8.10.

My gedit version: gedit 2.26.1 Ubuntu 9.04.

How reproducible:
Every time

Steps to Reproduce:
1. gedit <my file>
2. File -> Save
  
Actual results:
See above.

Expected results:
File has been saved without error message.

Directory Permission containing the file used in my example:
drwxr-xr-x 2 brian brian 4096 2009-05-11 17:55 notesTemp/

File Permissions of the file used in my example:
-rw-rw-r-- 1 brian brian 10095 2009-04-02 22:12 tempnotes.txt

Problem originally referred to in post:
[http://ubuntuforums.org/showthread.php?t=284798](http://ubuntuforums.org/showthread.php?t=284798)

---

### Post by wastvedt on 2010-01-28
Any news on this? Did you ever find a fix? I'm having the same problem on Karmic.

---

### Post by wastvedt on 2010-01-28
Sorry for the double post. I have this issue, but it is particular to my Desktop folder. My home folder is on a separate ext3 partition (/ is on an ext4 partition). Permissions are the same (766) on both the Desktop folder (with problem) and Documents (without problem). Any ideas or more information needed?

---

