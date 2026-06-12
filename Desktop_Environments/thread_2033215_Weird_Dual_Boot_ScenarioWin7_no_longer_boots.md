---
title: "Weird Dual Boot Scenario/Win7 no longer boots"
date: 2012-07-25
forum: Desktop Environments
---

### Post by rollerman2006 on 2012-07-25
I've had Ubuntu 12.04 dual boot installed via WUBI on my Win7 HP laptop for several months.

I primarily use Win7, using Ubuntu on the weekend and for Ruby on Rails.   

Recently Win7 crashed on me.  After the crash I can no longer boot up with Win7.   It reaches the welcome screen with Windows7 logo, freezes up and then reboots.

I've unsuccessfully attempted to repair Win7 via the repair option on  the Win7 install disk.  It simply fails to repair.   I've even attempted  to restore via my earlier imaging copy with no luck.

I AM able to boot up Ubuntu without any issues, eliminating the hard drive as the probable cause AND fortunately I've been able to grab all of my important data stored in Win7 via the HOSTS folder in the Ubuntu file system and copy it over to a external USB hard drive.

I'm resigned to the fact that I most likely will need to re-install Win7.   I even attempted to fix partition via GPARTED.   It recognizes that there is a problem in that partition but is unable to correct it.

Any other suggestions on how I could repair by Windows boot sector or should I just throw in the towel and re-install?   

I know that this post probably belongs in a Win7 forum, but it seems that Ubuntu does everything magically... any suggested tricks?

...and I am seriously thinking of ditching Win7 entirely if I could replace it with something that will natively  run my TV tuner and play Netflix.      I currently do this via VirtualBox under WinXP....which I also use to support my...I'm embarrassed to say..Microsoft Zune.    Let the mocking begin!

(I DO love my Zune, but it only runs Zune software, which only runs under Windows.)

Thank you.

---

### Post by oldfred on 2012-07-25
Normally we do not change user names, but you have used an email address. We try to delete email addresses as the amount of spam you get from those who scan the forum will be unbearable.

Please post a request in Forum Feedback & Help to have your name changed. Only an Admin can do that.

---

### Post by efflandt on 2012-07-25
Have you tried doing **chkdsk /f c:** from Win7 install disc?  Sometimes fixing Windows boot from the Win7 install disc takes several attempts before it is successful, but I have never used Wubi, and do not know if Windows would understand what to do with that.

If you do reinstall Win7 use Windows own Disk Management in Administration Tools to shrink the Windows partition and make room (unallocated space) to install Ubuntu on separate partition(s).  That can keep things separate so one will not affect the other.  But Ubuntu should still be able to access your Windows partition with a click of the mouse in the file manager as long as you stick to standard partitioning (not Windows volumes).

---

### Post by oldfred on 2012-07-25
If you have saved a lot of data in Ubuntu you need to back that up or back up the entire root.disk at that is wubi. Reinstalling Windows will also delete wubi.

If you have decided you like Ubuntu enough to keep it around it may be time to change to a partitioned install.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

If you just did the auto repair in Windows 7, you may need to run it again. It often takes at least three tries or using the manual commands. Even chkdsk often has to be run more than once as it does not always fix everything on one pass.

---

