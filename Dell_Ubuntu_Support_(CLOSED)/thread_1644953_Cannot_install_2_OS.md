---
title: "Cannot install 2 OS"
date: 2010-12-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by raac on 2010-12-13
Hi guys, I'm running into a situation where it won't let me install ubuntu along with Windows 7. I have an Inspiron 1525. The weird thing is that I did it once and it worked, but then I deleted the partitions (both ubuntu and windows 7) with the given CDs from my laptop (Windows Vista), then I installed the drivers, and then I upgraded to Windows 7 again. Once I did that I tried to install ubuntu along with it, but after I set up the size of the partition for ubuntu it threw an error saying there was an error in writing data or something like that (It won't let me create the partition for ubuntu). I don't know how to fix it, a buddy told me to delete the partitions from the command line (instead of the GUI of the given CDs) but I'm not sure how to do it, and if that will fix my problem.
 
Any ideas?
 
I don't know a lot of technical stuff so I'd appreciatte if you give details please
 
Thanks a lot.

---

### Post by ugm6hr on 2010-12-14
When installing Ubuntu, did you use the Ubuntu CD to resize W7?

---

### Post by raac on 2010-12-14
I'm not sure what do you mean by resize W7. But, I didn't get to install ubuntu, I didn't get passed the partition section. The error is before installing ubuntu.

---

### Post by ugm6hr on 2010-12-14
> **raac said:**
> I'm not sure what do you mean by resize W7.

Did you resize the Windows 7 partition with the Ubuntu CD?

---

### Post by raac on 2010-12-14
Oh ok, sorry. Yes, I attempted to, but it did not work. My hard disk is 250GB and Windows 7 is taking all of it. I wanted ubuntu to take 100GB and Windows 150GB, but that is when the error occured. Even though that error occurred I can still run Windows 7, so the Windows partition wasn't affected (Still 250GB). And yes I tried to do all that with ubuntu 10.10 CD.

---

### Post by nm_geo on 2010-12-14
> **raac said:**
> Oh ok, sorry. Yes, I attempted to, but it did not work. My hard disk is 250GB and Windows 7 is taking all of it. I wanted ubuntu to take 100GB and Windows 150GB, but that is when the error occured. Even though that error occurred I can still run Windows 7, so the Windows partition wasn't affected (Still 250GB). And yes I tried to do all that with ubuntu 10.10 CD.

It is recommended that you shrink your Window7 or Visa partition with the Windows disk Management Tool and using the free space you create to install Ubuntu.. Windows XP has no such tool so GParted work well shrinking the Windows partition.  Always reboot your computer immediately after shrinking your window partition and you should see ChkDisk run and then go into normal boot.

---

### Post by ugm6hr on 2010-12-15
> **raac said:**
> Even though that error occurred I can still run Windows 7, so the Windows partition wasn't affected (Still 250GB).

I would suggest you back up any necessary files, and then try and shrink the partition from within Windows 7.
Then try and install Ubuntu afterwards into the empty space (which you will have to manually create new partitions for).

---

