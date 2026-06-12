---
title: "Monitor screen resolution: Issue with older monitors"
date: 2010-11-02
forum: Desktop Environments
---

### Post by brspradeep on 2010-11-02
Hi,
I am new to Ubuntu and also on tight budget.
I have a old Pentium III box with equally old monitor (It says LG Sutdioworks 45v).
I have installed Ubuntu 10.04 LTS.
I have found it difficult to setup my screen resolution. It shows by default 800x600.
After some tweaking I can stretch upto 832x624.
I have seen resolution up to 1024x768 in windows on the same box and same monitor.

How can I improve the resolution? 
I have searched and found out that i need a xorg.conf setup as Ubuntu cant identify
my monitor properly.
I also installed ddcprobe, read-edid.
However I have met with limited success.

I am not aware of the driver I have.
How do I find out in Xorg.0.log?

Thanks,
Srinivasa Pradeep

---

### Post by h4xor66 on 2010-11-03
have you checked to see if there are third party drivers available for your video card ?  like the nvidia drivers

---

### Post by h4xor66 on 2010-11-03
by the way if you dont know how to do that go to 
System-->Administration-->Hardware Drivers ... it searches the system for drivers then produces the result: if it comes up with results for nvidia make sure the suggested driver is checked then click activate

---

### Post by warjowuch on 2010-11-04
If you have allready done that, you might want to deactivate the drivers, uninstall, reboot, and activate again.
After that, make sure you turn on your monitor while your pc is booting. It can error when it's initializing the screen, and the monitor is turned off.
Especially that seems to be the case with CRT-monitors.

Also, if you search around, other people have had the problem of an at first, correct resolution, and after a while, it gets bad again (indeed 800x600). I have solved this issue by blacklisting some nvidia modules, which do not belong to the proprietary driver, but fight for attention and screw things up. Search around, you'll find it.

----
But of course, I said this all with the pre-assumption of you having this trouble, while you might just have installed an immediately have this trouble. THen you might have no use for my comments :)

---

