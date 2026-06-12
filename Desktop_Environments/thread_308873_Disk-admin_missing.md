---
title: "Disk-admin missing"
date: 2006-11-28
forum: Desktop Environments
---

### Post by joplass on 2006-11-28
Dapper had a tools that one could use to mount disks.  The tool's name was disk-admin or disk-manager and was in System => Administration.  This tool is  missing in Edgy.  
Is there a way to install it in Edgy?  If not, is there a replacement?
Thank you,

---

### Post by deanAZ on 2006-11-28
There is a recent thread that addresses this topic:

[http://ubuntuforums.org/showthread.php?t=285279&highlight=missing+disks](http://ubuntuforums.org/showthread.php?t=285279&highlight=missing+disks)

I followed the suggestions and was able to add an additional storage drive.

Try - 

sudo apt-get install gparted
sudo apt-get install ptsdm

Then from the System -> Administration menu you will find
GNOME Partition Editor & Storage Device Manager

Good luck.

---

