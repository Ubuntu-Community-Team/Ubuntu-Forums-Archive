---
title: "Dell 5520 WWAN drivers for XPS M1330?"
date: 2007-12-08
forum: Dell  Ubuntu Support
---

### Post by iolalog on 2007-12-08
Hi guys

I just installed Ubuntu 7.10 on my XPS M1330 notebook, and it seems to work well. I do not have Internet access in the traditional way however, so I use the WWAN card with a 3G connection. This works very well in Windows,  but I have no idea how to set it up in Linux. Are there any drivers/tools to use, or am I out of luck for now? Thank you in advance for any help!

On a slightly related note, is there an easy way to setup 5.1 speakers on the system? I never managed on my XPS M1210, as the suggestion in the Ubuntu guide didn't work, and this is what stops me from using Ubuntu as my primary OS.

---

### Post by JoSch on 2008-01-05
+1 to that question

the card uses the same qualcom chipset as the sierra wireless MC8775 - so maybe try modprobe sierra?
I think a new device like /dev/ttyUSB0 has to be created for AT communication with the modem.

---

### Post by mk4umha on 2008-05-06
Did you guys ever figure this out to get it working?

---

### Post by motin on 2008-06-24
Did you get it working yet?

The most thorough thread on the forums on this subject is currently: [http://ubuntuforums.org/showthread.php?t=740888](http://ubuntuforums.org/showthread.php?t=740888)

---

### Post by mk4umha on 2008-06-24
Yep, I did, thanks for the link though. :)

---

