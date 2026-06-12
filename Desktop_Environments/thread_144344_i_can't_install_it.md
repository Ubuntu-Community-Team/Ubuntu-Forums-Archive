---
title: "i can't install it"
date: 2006-03-14
forum: Desktop Environments
---

### Post by raker on 2006-03-14
i try to install iso-install breezy badger 5.10...boot from cd...and stops...the last line was...
      ata 1: dev 0 ATA, max UDMA/133, 234441648 sectors:     lba 48
...what must i do?

---

### Post by OffHand on 2006-03-14
Did you check the md5sum of the download?
I believe you check it with md5sum <filename>
How fast did you burn the disk? Full speed usually doesn't give the best results.
I'm not an expert... just poking around.

---

### Post by raker on 2006-03-14
how can i verify it with md5sum...i have only xp...i must write this when i boot from cd at the beginning...

---

### Post by OffHand on 2006-03-14
I found this with Google: [http://www.etree.org/md5com.html](http://www.etree.org/md5com.html)
and this: [http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

---

### Post by Sutekh on 2006-03-14
Try [Win MD5 Sum]("http://www.nullriver.com/index/products/winmd5sum")

I used this in Windows.  Also make sure that the CD is burnt as an image, not a data disc, not a bootable disc.

Check it against this [http://mirrors.uwa.edu.au/ubuntu-releases/5.10/MD5SUMS]("http://mirrors.uwa.edu.au/ubuntu-releases/5.10/MD5SUMS")

---

### Post by raker on 2006-03-14
true...but it can not runs on xp :(

---

### Post by Sutekh on 2006-03-14
Try [Win MD5 Sum]("http://www.nullriver.com/index/products/winmd5sum")

This runs on Windows

---

### Post by raker on 2006-03-14
thanks a lot...i burn it as image..now i'm trying to verfiy with MD5SUM

---

### Post by raker on 2006-03-14
and if MD5 Sums are different,...means that does't works and i need another ubuntu iso install?

---

### Post by mozetti on 2006-03-14
Yes - the MD5 checksum is a hash generated from the original. If the checksums don't match, it means the disc you burned doesn't match the original. Try re-burning the iso at a slower speed. If you wanna be ultra-confident, try the lowest burn speed.

---

### Post by raker on 2006-03-14
but evrey image which i try failed at compare with md5 sum...can u help me with a good link

---

### Post by Sutekh on 2006-03-14
Check the MD5 sum *before* you burn it not after.  If the MD5 sum does not match, then you will need to download the ISO again.  

This has happened to me once or twice.  I would really recommend downloading the ISO with a download manager or by bittorrent.  I had problems downloading straight from Firefox.

What software do you use to burn the disc?

---

### Post by raker on 2006-03-14
i have tested it with that program and it works...and is the same thet i burn on cd...

---

### Post by Sutekh on 2006-03-14
OK so the MD5 sums match?  That's good

What are software are you using to burn the disc?

---

### Post by raker on 2006-03-14
i burn it with nero and download with firefox...it was my fault..it works md5 sum...but still fail at install

---

### Post by raker on 2006-03-14
nero-burn image...and open...than burn

---

### Post by OffHand on 2006-03-14
Try burn it again at 4 speed. Maybe your CD is fooked somehow.
If the md5sum is ok the iso should be fine.

---

