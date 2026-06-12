---
title: "Nautilus and HD"
date: 2006-09-19
forum: Desktop Environments
---

### Post by esquilo on 2006-09-19
Hi Guys,
The "COMPUTER" in Nautilus doesn't shows my second HD icon. It's just shows the floppy disk, Cd-rom em the first HD icons. If I want to access it,I'm going to  /mnt/hdb1 directory. How can I introduce the second HD icon in  "Computer" to make my life easy?

regards!


My /etc/fstab is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1 /mnt/hdb1 reiserfs defaults,auto        0       2 ->> this is my second hd!

---

### Post by whitewizardcoder on 2006-09-19
I believe that all mounted drives that appear in the "Computer" must be mounted in "/media/".  Try changing "/mnt/hdb1" to "/media/hdb1" in your fstab.

You will also have to make a "/media/hdb1" directory:
```
sudo mkdir /media/hdb1
```

Then try rebooting.

Hope this works!

-WhiteWizardCoder

---

### Post by esquilo on 2006-09-19
[COLOR="Black"][/COLOR]

That's Work! Thanks!

---

