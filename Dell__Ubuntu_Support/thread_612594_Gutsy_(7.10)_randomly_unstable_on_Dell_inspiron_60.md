---
title: "Gutsy (7.10) randomly unstable on Dell inspiron 6000"
date: 2007-11-14
forum: Dell  Ubuntu Support
---

### Post by joepnaus on 2007-11-14
I am  experiencing stability problems. Installed Gutsy 7.10 two weeks ago my Dell Inspiron 6000 laptop and about three times a day the system hangs. I can't reproduce the fault. No clear cause. About a month ago I installed Feisty 7.04 and this gave the same problem. I hoped this would be a problem that would be solved in 7.10 - nope. 

Further characteristics are that the screen freezes and only the mouse cursor moves. The only option then is a hard reboot. 

Some old thread (somewhere) described simular problems with some older Ubuntu version. Had to do with repetative polling of the CDROM drive. This was testable with keeping a cdrom in the drive. To be short on this. This test did not resolve the problem. 

Please anyone help.

---

### Post by dacap06 on 2007-11-14
Joe,

I have seen this behavior sporadically on systems running Linux where the Advanced Programmable Interrupt Controller isn't implemented exactly right.  There can be a wealth of other causes too.  I had an off-brand nVidia controller that caused exactly the same symptoms.  Going with the assumption that it's an APIC issue, try the following:

1) Either at the command line, or using the "run command" menu entry, run gksudo gedit (or substitute your favorite graphical editor).  You must have root privileges to edit this file, ergo the use of gksudo in Gnome - or use kdesu in KDE.

2) Open /boot/grub/menu.lst.  We are going to add some kernel parameters to the boot line.

3) At the end of each line listing the kernel, add the words "noapic nolapic" at the end, as in the example shown below.  Either the change will fix the problem or it will effect no change if your APICs are not the problem.

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=4f146ca4-8f7f-47c4-a72e-e19e101288cd ro quiet splash **noapic nolapic**

4)  Save the file and reboot.

---

### Post by joepnaus on 2007-11-15
I've tried your suggestion on changing the entries in the menu.lst file but painfully my system already hung two times this short morning. Sorry to say that it does not seem to work.

Mentioning the NVIDIA issue, I do have a *restricted driver* issue on my NVIDIA driver. It concerns the driver for hardware acceleration for the ATI card. For the moment I am not using it since the Compiz fun stuff doesn't work then. 

I will try to use the restricted driver - but not earlier then this evening (restrict internet access at work spot). For this moment I turn of Compiz since my problem looks a bit like: [http://ubuntuforums.org/showthread.php?t=587905&highlight=restricted+driver+ATI]("http://ubuntuforums.org/showthread.php?t=587905&highlight=restricted+driver+ATI")

---

### Post by joepnaus on 2007-11-20
It seems the ristricted driver solves a great deal of the problems. A pitty I now miss all the Compiz fun stuff. Anyone who knows the answer to this? Stable system and Compiz stuff???

I've noticed that Google Earth works fine with the restricted driver but does not work with the unrestricted-Ubuntu own driver!! This is also a known issue. What to do?

---

### Post by thecure on 2007-11-24
> **joepnaus said:**
> It seems the ristricted driver solves a great deal of the problems. A pitty I now miss all the Compiz fun stuff. Anyone who knows the answer to this? Stable system and Compiz stuff???

I've noticed that Google Earth works fine with the restricted driver but does not work with the unrestricted-Ubuntu own driver!! This is also a known issue. What to do?

One of my laptops is an Inspiron 6000 and it has the least amounts of freezes with compiz-fusion. (The integrated Intel seems to work better and faster than the dedicated NVidia card!) 
Depends on how much you want to try but I would recommend reinstalling ubuntu-desktop with aptitude or even a clean installl. The rare times the desktop freezes on me there is no mouse movement-everything freezes, so I would expect not just a driver issue. Does your freezes happen when you run an OpenGL program? If so just turn of desktop effects before running; then back on after.

Later.

---

### Post by raxso on 2007-11-24
I am also experiencing this on my Inspiron 6400 using Kubuntu 7.10. it is unstable on my system.

---

### Post by joepnaus on 2007-11-25
> Depends on how much you want to try but I would recommend reinstalling ubuntu-desktop with aptitude or even a clean installl. The rare times the desktop freezes on me there is no mouse movement-everything freezes, so I would expect not just a driver issue. Does your freezes happen when you run an OpenGL program? If so just turn of desktop effects before running; then back on after.

My system became remarkably stable since I'm using the restricted driver. I just once mistook and marked a very very busy for been freezed-up. So to be honest,  has been stable since then. I'm using xserver-xgl now to run compiz on the restricted driver and that just works fine - though - performance ran a bit down - though - acceptable. 

In different posts it has been written that a new ATI driver is to be expected any moment. Would it be wise to wait for this? Since I am a linux-novice is seems daring to reinstall ubuntu-desktop. By the way. 7.04 gave me the same freezes.

---

### Post by blue-maya on 2007-12-05
Hi Guys,

the problem is related to the same problem 64bit Linux users are experiencing. There is a big forum thread about it. No solution yet....

---

### Post by thecure on 2007-12-06
> **joepnaus said:**
> r.

In different posts it has been written that a new ATI driver is to be expected any moment. Would it be wise to wait for this? Since I am a linux-novice is seems daring to reinstall ubuntu-desktop. By the way. 7.04 gave me the same freezes.

My Inspiron 6000 has integrated** Intel** video. And so ATI will not work if you have the same.

Later.

---

### Post by joepnaus on 2007-12-07
In the meantime I've installed the new ATI driver and the system seems stable and Compiz stuff is working technically well. But... Firefox (and some others) scroll really slow and video playback troublesome. These failures very already mentioned on the forum. Seems we have to wait a bit more.

---

