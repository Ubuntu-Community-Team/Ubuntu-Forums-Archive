---
title: "[SOLVED] best way to backup home dir?"
date: 2008-12-23
forum: General Help
---

### Post by firsttimeuser on 2008-12-23
I am going to upgrade to kubuntu8.10 and want to backup all the stuff under my home directory, so what is the best way to do this backup? Just

"cp -R myhome /media/external disk" after I login into the system?

Or should I boot the system into single user mode then do the "cp -R" thing?

---

### Post by Titan8990 on 2008-12-23
I would use rsync:


rsync -av /home/USERNAME /media/external\ disk


You may have to use sudo if your user doesn't have permission to write to the external drive. Unless the external drive is ext2 or ext3 your permissions will not be preserved.

---

### Post by pennacook on 2008-12-23
Should be ok with the first option.

---

### Post by firsttimeuser on 2008-12-23
so do you think it is necessary for me to boot into single user mode? Last time i used "cp -R" command but somehow not all the files had been copied over and I don't know why. 

 
> **Titan8990 said:**
> I would use rsync:


rsync -av /home/USERNAME /media/external\ disk

---

### Post by Titan8990 on 2008-12-23
> so do you think it is necessary for me to boot into single user mode?


Not at all.

---

### Post by hyper_ch on 2008-12-23
I'd use rsync

---

### Post by firsttimeuser on 2008-12-23
thanks a lot, guys! looking into the manpage of rsync now

---

### Post by compman25 on 2008-12-23
Or you can use Home User Backup

---

