---
title: "3D Desktop that works with ATI propr.driver?"
date: 2006-11-27
forum: Desktop Environments
---

### Post by camilluk on 2006-11-27
I read different posts about this, and I get conflicting opinions/impressions. Can anyone please confirm whether Beryl, for instance, works with the proprietary ATI driver (eg. version 8.31*)? Or does it only work with the open source ATI driver?

If Beryl does not work, can anyone suggest a 3D desktop that works with ATI's proprietary driver?

Thank you!
Cam

---

### Post by drphilngood on 2006-11-27
Although I don´t use it, I´m sure it does use the proprietary driver but I´m not sure what version/s.  In addition, [Compiz]("http://en.wikipedia.org/wiki/Compiz") or [3ddesktop]("http://desk3d.sourceforge.net/") are alternatives.  Finally, although the [Beryl site]("http://forum.beryl-project.org/") is down, you can still find all the info and links you need at:

[One thread to rule them all v2: Beryl & Official Compiz]("http://ubuntuforums.org/showthread.php?t=272104")

Hope this is satisfactory.

Good luck!

---

### Post by Rob2687 on 2006-11-27
If you are using the propietary driver you must run Xgl. Otherwise if you are using the open source driver then you must use aiglx

---

### Post by camilluk on 2006-11-27
> **Rob2687 said:**
> If you are using the propietary driver you must run Xgl. Otherwise if you are using the open source driver then you must use aiglx

And how do I tell my pc to use Xgl? :oops:

I read [One thread to rule them all v2: Beryl & Official Compiz]("http://ubuntuforums.org/showthread.php?t=272104") and it says that one should use the open source driver. Enabling Xgl with the proprietary driver means I can run Beryl? Or perhaps another 3D-DE?

---

### Post by Random20230808 on 2006-11-27
Try out this thread : [https://help.ubuntu.com/community/CommonQuestions#head-23187ff8609335c10dbb55c6cdc4c1f47fddcda0]("https://help.ubuntu.com/community/CommonQuestions#head-23187ff8609335c10dbb55c6cdc4c1f47fddcda0")
It is very helpfull.
Read out the [Hardware]("https://help.ubuntu.com/ubuntu/desktopguide/C/hardware.html") section too (it's in the thread).
I have managed to run Xgl/Beryl using the proprietary driver.
I haven't given much of a try on Aiglx but Xgl works fine for me.
However I had a few problems regarding my graphic card bur I searched some threads and found the solutions (e.g. before installing Beryl, Xgl made my desktop running slowly).
Try the above tutorial from official ubuntu documentation and if you have problems write back.

---

### Post by Rob2687 on 2006-11-27
If you're running a pretty recent ATI card (like 9500 and newer) then you're better off using Xgl and the propietary drivers.

---

