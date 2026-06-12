---
title: "Removing 9.04 and Studio"
date: 2009-05-10
forum: General Help
---

### Post by crazyk on 2009-05-10
My laptop has Vista, Ubuntu 9.04, AND Ubuntu Studio installed.  I'm selling this computer and my thought was to use Dban and reinstall Vista using the Recovery Discs that I made when I first got the machine.  

Will using Dban cause me to lose the ability to recover Vista?  I assume Dban would also delete the recovery partition.  Or does Dban have an option to not erase the recovery partition?  


Or...is there an easier way to remove the two Ubuntu Operating Systems?

---

### Post by raymondh on 2009-05-10
> **crazyk said:**
> My laptop has Vista, Ubuntu 9.04, AND Ubuntu Studio installed.  I'm selling this computer and my thought was to use Dban and reinstall Vista using the Recovery Discs that I made when I first got the machine.  

Will using Dban cause me to lose the ability to recover Vista?  I assume Dban would also delete the recovery partition.  Or does Dban have an option to not erase the recovery partition?  


Or...is there an easier way to remove the two Ubuntu Operating Systems?


since you want to retain Vista, why not just use Vista's disk management program to delete the linux partitions and then expand the Vista partition?

I don't know about dban, sorry.  

Don't forget to fix the MBR for Vista

BTW, using Vista's disk manager, you cannot extend to the left.... only to the right.  That means, delete the rightmost partition first.

Just my 2 cents.

---

### Post by hansdown on 2009-05-10
Hi crazyk.

Be careful!

Recovery disks are NOT the same as install disks.

If you dban your drive, you will not be able to reinstall with these

disks.

Download gparted, and burn a disk.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

This should help.

[http://video.google.ca/videosearch?q=removing+ubuntu+and+keeping+windows&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&ei=sXcHSpHHPKaAtgO10ODoAQ&sa=X&oi=video_result_group&resnum=5&ct=title#](http://video.google.ca/videosearch?q=removing+ubuntu+and+keeping+windows&oe=utf-8&rls=com.ubuntu:en-US:unofficial&client=firefox-a&um=1&ie=UTF-8&ei=sXcHSpHHPKaAtgO10ODoAQ&sa=X&oi=video_result_group&resnum=5&ct=title#)

---

