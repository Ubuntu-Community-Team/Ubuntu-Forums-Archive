---
title: "Problem Writing ISO"
date: 2012-12-06
forum: Development CD/DVD Image Testing
---

### Post by saide18 on 2012-12-06
Please some one tell me what could possibly went wrong; I was writing Ubuntu 12.04.iso(695MB) to a CD-R(700MB): writing completed successfully: It showed "success".
Then disk check or checksum was going on : It needed 15 minutes of time ; I went on to have a cup of coffee and came back and saw that it said "Error while checking : the data might be corrupted" . what the heck could have happened?

---

### Post by verzx on 2012-12-06
Maybe the ISO is corrupt or the disc may of been formatted incorrectly.

Check this out: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by powder on 2012-12-09
Try burning from command line. It's been more reliable for me.

```
wodim dev=/dev/cdrw -dao -eject -v image.iso
```

---

### Post by manhpv12 on 2013-03-06
Maybe the ISO is corrupt or the disc may of been formatted incorrectly.

---

