---
title: "The good old installation problem"
date: 2005-12-30
forum: General Help
---

### Post by rikard_grankvist on 2005-12-30
Hello. I know this has been discussed before, but the advice I've gotten hasn't worked. It's the classic DEBOOSTRAP error.
"DEBOOTSTRAP has exited with an error (return value 1), base install failed, error log in /target/var/log/debootstrap.log" or something to that effect. Most people say it's a bad cd, but I've tried with four CD's now, two ShipIt and two burnt ISO's (one of them burnt at slowest speed). The problem always occurs at the exact same place in installation, 26 % or so of base install. It seems to me that if it were bad cd's, they shouldn't all give the same error at the exact same spot.
I also can't look at the error log for some reason. When I open a console and go to the folder where it's supposed to be, that folder is empty.

If someone has an idea what this might be, I would be really thankful. Or if someone knew how to extract the error log.

---

### Post by az on 2005-12-30
You can see the errors on virtual colsole three.  Hit CTRL-ALT-F3 wjust before it borks and post what you see.

---

### Post by barbex on 2006-01-05
Just in case it helps somebody:

The error occured for me because I hade made my root partition too small (20MB instead of 20GB *slaps forehead*).

Now it works!

---

### Post by rikard_grankvist on 2006-01-07
Ok. Thanks. The error message is "tar: /usr/share/man/man3/Locale::gettext.3pm.gz: Invalid argument". Same problem as this guy: [http://www.ubuntuforums.org/showthread.php?t=109642](http://www.ubuntuforums.org/showthread.php?t=109642) has. However, my live-CD works perfectly. And as I said, I have double checked the integrity of the CD. What does the error message mean?

---

### Post by rikard_grankvist on 2006-01-26
YES!!! I solved it. I didn't know that you can't have FAT32 as the file-system of the root partition. That was the only error. When I fiddled around a bit and tried ext3 instead, it worked beautifully. Perhaps other people suffering from the DEBOOTSTRAP error have made the same mistake.

---

