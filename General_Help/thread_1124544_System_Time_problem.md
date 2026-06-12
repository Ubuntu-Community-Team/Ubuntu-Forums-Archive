---
title: "System Time problem"
date: 2009-04-13
forum: General Help
---

### Post by djbushido on 2009-04-13
Okay, so my Linux machine detects system time fine, but sets it 4 hours ahead (eastern time). This is a problem for people who use Windows on the same system. Is there a way to fix this? I can make it so that the Linux is wrong, but I would prefer both to be correct.

---

### Post by LowSky on 2009-04-13
Its an odd problem but easily fixed. Go into BIOS and make sure the system time is correct, most likely it is not. Then boot into Windows and update the time. Make sure by rebooting that he time is correct. then boot into Linux and check the time. Then  in an hour os so reboot back into Windows, all should be good, if not change the clock sync options from Windows

---

### Post by djbushido on 2009-04-13
Yup, as expected the BIOS time was off. Will post back later if this works.

---

### Post by djbushido on 2009-04-16
Okay, not fixed. I reset the BIOS Time (really CMOS I guess...), but when I ran linux, it set the BIOS time backwards 4 hours (I am on Eastern Time: GMT - 4). I think setting Linux to using Central Time, or GMT would fix the problem, but then Linux would be messed up. Is there a way that I can tell the system to just use the BIOS time?

---

### Post by dohcdoh on 2009-04-20
I have the same question: How do you Ubuntu to sync with the BIOS time? I have Ubuntu 8.10.

I probably would not have noticed this except I had to change the motherboard battery. Here is the problem. The BIOS time is set to the correct time, i.e. 8:00 A.M. Ubuntu is booted. Ubuntu shows the time as 2:00 A.M. A Boot to Puppy Linux shows the current BIOS time of 8:00. In other words, Ubuntu displays a time that is 6 hours earlier than the BIOS time. How is that possible?

---

### Post by djbushido on 2009-04-20
It's quite possible that Ubuntu is using a time zone setting that Puppy is not.

---

### Post by CatKiller on 2009-04-20
> **djbushido said:**
> Is there a way that I can tell the system to just use the BIOS time?

I believe that setting UTC=no in /etc/default/rcS does this.

---

### Post by dohcdoh on 2009-04-20
djbushido,

Different time zone would not have that effect. The system time is not zoned.

CatKiller,

Your UTC info put me on the search and I found my fix here:

From "Unofficial Ubuntu 6.10 (Edgy Eft) Starter Guide"

 How to disable system time/date from being reset to UTC (GMT)
 

sudo cp /etc/default/rcS /etc/default/rcS_backup
gksudo gedit /etc/default/rcS

    * Find this line 

...
UTC=yes
...

    * Replace with the following line 

UTC=no

    * Save the edited file
    * System -> Administration -> Time and Date 

Set the correct time/date

sudo /etc/init.d/hwclock.sh restart

Thanks for the help!

---

### Post by djbushido on 2009-04-20
Will try this.
Note for anybody that tries this, please back up the rcS file! Please!

---

