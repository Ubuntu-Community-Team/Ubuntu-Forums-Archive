---
title: "New Dell Inspiron 530n - Hardware problem or known issue?"
date: 2008-03-10
forum: Dell  Ubuntu Support
---

### Post by al_mckin on 2008-03-10
Hi everyone,

I recently recieved a new Dell Inspiron 530n.  It was supposed to come with Ubuntu but due to any admin error it came with no operating system at all!

I downloaded the dell reinstall .iso and had mixed results.
First boot ended up dropping to a shell, i think there were some ata timeout error messages and some of these:

failed to set xfermode (err-mask = 0x40)

Also strangely, each keyboard press registered two presses on the screen, making the shell unusable.

Next boot, I first saw some usb errors, then more ata errors. Third boot, everything went fine and ubuntu installed perfectly. The computer hung on first reboot after install, cant remember exactly where.

Googled a bit, added irqpoll to the command line as a result and now everything is hunky dory.

So, is this a known issue for anyone?  Also saw this bug in Fiesty:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang")

Could this be related or is it more likely I have a hardware problem?

Best regards and thanks,

Alastair

---

### Post by notwen on 2008-03-11
Curious, did you contact Dell regarding your OS-less system?  If one thing was not accurate, it's quite possible that there are more things that may not be accurate.  When you say no OS, I'm guessing no Ubuntu, no FreeDOS, no anything correct?  

I'm glad you glad you got your system up & running, but I prefer to get what I ordered out of the box.  Which re-install iso did you download by chance, because these issues did not seem o make their way into Gutsy installs on the 530n.

---

### Post by freddybob on 2008-03-11
I had this problem on my 530n.

The solution (for me) was to plug the keyboard and mouse into the lower USB ports on the back of the machine (the problem only occurred when using the upper two USB ports).

---

### Post by al_mckin on 2008-03-13
Well looks like the problem is sorted...

I haven't contacted Dell yet, but that is on the radar!  In fact, I spoke to a Dell linux support rep and he advised me to conact them even if it was working.

I downloaded the iso here:

[http://linux.dell.com/files/ubuntu/iso-images/ubuntu-dell-530n-nvidiavideo-reinstall.iso](http://linux.dell.com/files/ubuntu/iso-images/ubuntu-dell-530n-nvidiavideo-reinstall.iso)

It all seemed to work after I performed the steps outlined here:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/USB-SATA_race_condition_causes_hang)

It might even be a total conincidence that it worked.  I first got it booting with "irqpoll" on the kernel command line, then after performing the fix above, I didnt need that any longer.

However, all of this is circumstantial evidence!  

I didnt try the usb ports thing, but my keyboard and mouse were certainly in the top two ports so it is a possibility!

---

