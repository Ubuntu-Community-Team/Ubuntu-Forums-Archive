---
title: "Help me format my USB Drive"
date: 2009-04-25
forum: General Help
---

### Post by daisyfoofpoof on 2009-04-25
I was trying to format my USB Drive (Don't ask why) and now it's not working lol.  It was originally a Kingston 1GB Datatraveler with one fat16 partition with the label 'KINGSTON' and the mount point /media/KINGSTON.  I tried to recreate this, but now my computer sees it as an scsi drive it can't mount...PLEASE HELP!!!!!

---

### Post by StOoZ on 2009-04-26
use GParted.

---

### Post by Dr_Willis on 2009-04-26
give details.. what filesystem did you want to format it To>

If you are wanting to use ext2 or ext3 on it. You must set the permissions and owndership of the files/directories after you format it - so they are owned by the person you want to have access.

for vfat/ntfs - this does not apply.

Gparted should allow you to do most of this.

---

### Post by platinumriver on 2009-04-27
See this thread

[http://ubuntuforums.org/showthread.php?p=7157528](http://ubuntuforums.org/showthread.php?p=7157528)

If GParted has the file systems you want greyed out, you just need to install support for those file systems.

---

