---
title: "i/o error while copying dat files"
date: 2005-12-26
forum: Desktop Environments
---

### Post by hari78 on 2005-12-26
what shall be the entry in fstab to copy all kinds of files from a cd? presently i am unable to copy or view .dat files. this is the entry concerned in fstab

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
 any one, plz help
thanks in advance

---

### Post by Sutekh on 2005-12-26
What is the output of
```
df -h
```
I don't think /dev/scd0 is the correct location for your cd drive, on my PC it is /dev/hdc, as seen from df -h
```
/dev/hdc  653M  653M  0  100%  /media/cdrom
```
and my entry in /etc/fstab
```

/dev/hdc  /media/cdrom0  udf,iso9660 ro,user,noauto  0  0

```

See if you can use the output of df -h on your PC to determine the proper location.
Just change that bit, the rest of your entry is fine

---

### Post by hari78 on 2005-12-27
thanks for your reply,, it is changed accordingly. But still the problem persists for vcd files not for any other files. plz suggest further

---

### Post by true_friend on 2007-06-22
Buddy it is a bug. A know bug u can see [here ]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/82307")for more detail.

---

