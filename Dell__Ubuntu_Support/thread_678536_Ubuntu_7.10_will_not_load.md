---
title: "Ubuntu 7.10 will not load"
date: 2008-01-26
forum: Dell  Ubuntu Support
---

### Post by stcrowley on 2008-01-26
I've got a Dell D630 and I'm having a hard time getting the live CD to load.

I've tried this 2 different ways with the same results.

1. Burned Ubuntu 7.10 disk and booted to CD.  The Ubuntu options screen comes up but when I try to select any of the options other than Boot from first hard drive, nothing happens.

2. I've tried loading the CD within MS Virtual PC, same results.

Has anyone seen this?

---

### Post by rosegarden78 on 2008-01-26
First time installing?  CD must be burnt at 4x or slower.  If you can't load LiveCD software not compatible.  But LiveCD more compatible with hardware than XP.  Everything should be OK follow [guides]("http://ubuntuforums.org/showthread.php?t=677959") [here]("http://ubuntuforums.org/showthread.php?t=385981") for Vista Mac desktop.  By the way I'm on a Dell Inspiron 1200 CeleronM 1.1Ghz 512MB with Intel 915GM graphics and these links work.

---

### Post by xeth_delta on 2008-01-26
May I also suggest reading the [Burning Iso How-to]("https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28")?

---

### Post by gbrainin on 2008-01-26
Make sure you check the MD5 sum on the downloaded file, and do an integrity check on the burned CD.  Problems with the download and/or burn happen with some frequency.

---

### Post by boyofford on 2008-01-27
If your using windows and want to do a md5sum check,
the winmd5sum is free and  does that really easy,
...heres a link to them...
[http://www.nullriver.com/index/products/winmd5sum](http://www.nullriver.com/index/products/winmd5sum)

---

### Post by rogi on 2008-01-27
If your installing Ubuntu, try using the Alternate CD.  the normal live CD had a hard time with the SATA controller on my XPS-M1330.  It would either hang the booting of the live CD or fail the install.

If your just playing with the LiveCD, try turning off some of the auto-detect features, esp ones dealing with the HDD.

---

