---
title: "Wierd Hard Drive Problems"
date: 2008-09-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jsmidt on 2008-09-20
For the last week or so the hard drive on my Dell Inspiron 1525 Laptop has been acting very strange. (I think it is the hard drive) 

1.  It keeps clicking all the time.
2.  After every(almost every) reboot or suspend I have to run fsck manually to fix several inode and other problems.
3.  Twice, upon rebooting the computer claims no hard drive is detected.  When I try to reboot again, it usually works, but I still have to run fsck manually.
4.  I reinstalled Ubuntu using Dell's re-install DVD and I still have the same problems?

Does anybody know if this sounds like a hardware or software issue?  Any ideas what I should do or try?  Thanks

---

### Post by jbloodwo on 2008-09-20
what does the click sound like and do you hear anything that might sound like you need to replace the brakes on your car?

but my general guess would be hardware. 

if you can fine a linux tool to access the drives SMART status you might be able to see if teh drive is reporting some type of error.

---

### Post by jsmidt on 2008-09-22
I don't know what SMART status.  Could you explain to me what this is and how I would try to understand it using tools.

---

### Post by jbloodwo on 2008-09-22
SMART is a drive monitering technology built in to ATAPI and SATA hard drives.  SAMRT will moniter thing like faild readwrites and things like that.  You can get more information on SMART at wikipedia including a chart of known SMART error codes. 
[http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology](http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology)

---

### Post by jsmidt on 2008-09-22
So I ran one of these SMART programs: Hard Drive Sentinel.  Below is the output.  It doesn't look good, however I don't know what almost any of the errors mean.  Is there anyone who can interpret this stuff.  Thanks.

```
    Hard Disk Summary
    -----------------
    Hard Disk Number. . . . . . . . . . . . . . . . .  0
    Hard Disk Device. . . . . . . . . . . . . . . . .  /dev/sda
    Interface . . . . . . . . . . . . . . . . . . . .  S-ATA II
    Hard Disk Model ID. . . . . . . . . . . . . . . .  ST9120823ASG
    Hard Disk Revision. . . . . . . . . . . . . . . .  3.ADD
    Hard Disk Serial Number . . . . . . . . . . . . .  5NJ0WXTF
    Hard Disk Total Size. . . . . . . . . . . . . . .  114473 MB
    Current Temperature . . . . . . . . . . . . . . .  45 °C (113 °F)
    Power On Time . . . . . . . . . . . . . . . . . .  76 days, 11 hours
    Estimated Remaining Lifetime. . . . . . . . . . .  0 days
    Health. . . . . . . . . . . . . . . . . . . . . .  -------------------- 0 % (Poor)
    Performance . . . . . . . . . . . . . . . . . . .  #################### 100 % (Excellent)

    Failure Predicted - Attribute: 7 Rate of positioning errors of the read/write heads. Indicate problem with servo, head. High temperature can also cause this problem.
    There are 119 bad sectors on the disk surface. The contents of these sectors were moved to the spare area.
    The drive found 30 bad sectors during its self test.
    There are 30 weak sectors found on the disk surface. They may be remapped any time in the later use of the disk.
    Replace hard disk immediately.
      It is recommended to backup often to prevent data loss.


```

---

### Post by nowshining on 2008-09-22
is the smart program u used a windows or linux app? if so where may i download it?

---

### Post by jsmidt on 2008-09-22
I used this:

[http://www.hdsentinel.com/hdslin.php](http://www.hdsentinel.com/hdslin.php)

---

### Post by nowshining on 2008-09-23
> **jsmidt said:**
> I used this:

[http://www.hdsentinel.com/hdslin.php](http://www.hdsentinel.com/hdslin.php)

nice find :)

---

### Post by jbloodwo on 2008-09-23
Looks like you should call customer care/tech support.

---

### Post by jsmidt on 2008-09-25
Well, since my laptop is under warranty, Dell sent me a new hard drive.  Everything works great!  Thanks Dell!

---

