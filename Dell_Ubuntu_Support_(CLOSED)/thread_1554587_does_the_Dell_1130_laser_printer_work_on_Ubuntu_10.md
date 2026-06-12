---
title: "does the Dell 1130 laser printer work on Ubuntu 10.04?"
date: 2010-08-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lue42x on 2010-08-16
I need a laser printer and I was thinking of buying from Dell because I heard they support Linux.  I checked the Dell site for info on driver support - unfortunately the page did not specify Ubuntu support.  It lists Redhat, and "various Linux distributions" ... but no specific mention of Ubuntu.

snip

Also, I found this page that says it does support Ubuntu 8.04, but it does not mention any newer versions of Ubuntu

snip

---

### Post by wdaniels on 2010-08-17
No doubt it will work fine with newer Ubuntu versions, since it is not a case of relying on proprietary drivers from Dell. Saying "Other Linux OS" probably just means it uses a driver from the standard open printing stack (as almost all printers do) but they only tested it on the specific listed distros. No reason to expect differently in newer distro versions.

---

### Post by lue42x on 2010-08-17
Thanks, that is comforting.  My only worry is that it won't work and I'll be stuck in the return-and-find-a-new-printer cycle when school starts..

I may still buy the Dell because it seems like it will most likely work based on your post ... any other opinions or even a Dell employee who may be able to confirm?

---

### Post by Unsk1ll3d on 2012-06-08
If this problem is still appearing, I have hacked the driver today and it's working with my 12.04 Ubuntu environment.

The official PPD didn't work, because it was for a too-old CUPS version and a very old Linux environment, so I had to manually create the rastertosamsungspl binary and patch some lines in the PPD file.

[https://github.com/martensms/dell1130-ubuntu](https://github.com/martensms/dell1130-ubuntu)

Greets,
Christoph

---

### Post by huguenant on 2012-10-23
Hello Christoph

I did used your PPD file for DELL 1130 with Ubuntu 8.0, and it worked fine.
But, with Ubuntu 12.04 and 12.10, I have problems, despite I have installed your new "install.sh. When it does not work, the solution I have found is to shut the printer down and up.
Could you give me some help.
Thanks.

---

### Post by #su~ on 2013-01-09
> **Unsk1ll3d said:**
> If this problem is still appearing, I have hacked the driver today and it's working with my 12.04 Ubuntu environment.

The official PPD didn't work, because it was for a too-old CUPS version and a very old Linux environment, so I had to manually create the rastertosamsungspl binary and patch some lines in the PPD file.

[https://github.com/martensms/dell1130-ubuntu](https://github.com/martensms/dell1130-ubuntu)

Greets,
Christoph

This worked awesome for me. We have an 1130n as a network printer, I'm now able to use it without using the crappy Dell drivers/utilities.

---

### Post by huguenant on 2013-01-30
Hello.
Thanks for your answer. I did soon used this patch. It works fine at first request, from time to time at second, and never at the third. I have to swtich the printer (dell 1130) nearly at each time off. 
Happy to read you.

---

### Post by Roland__Tremblay on 2013-10-09
Hello

We had been using this printer with 11.10 with no problems.  When we went to 12.04 we could not easily get it to work.  To make a long story short we found out that the Dell 1130 will work if you use the Samsung ML1915 from the maufacturer list of printers instead of the 1130 for this version of Ubuntu.

Roland Tremblay

---

