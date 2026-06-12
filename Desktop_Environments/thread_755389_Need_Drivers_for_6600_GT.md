---
title: "Need Drivers for 6600 GT"
date: 2008-04-14
forum: Desktop Environments
---

### Post by regalistic2003 on 2008-04-14
Hey guys I need help and hoping i came to the right place. I Just installed A dual boot of Windows XP Pro W/ SP2 And Ubuntu 7.10 (which I absolutely love) So far Everything has gone good, For some reason, I **can Not** Get my Gpu Drivers to install right,(6600 GT PCI Express 128 MB RAM) I've gone to Nvidia Site and downloaded the drivers but when i double click on the Desktop It says Wrong Driver File, or something in that sort or Driver File not Found, I'm totally lost is their a Run Command i need to do? I have a 22 LCD the Default Resolution is 1680 X 1050  and a 17 LCD Dell Monitor (1280X1024) That I would like to hook up as a dual monitors So far I've only achieved a lousy 800X600 Resolution on one monitor (22LCD)

So what i need is a Actual Driver that works In Ubuntu 7.10 For my 6600 Nvidia (bfg 128 MB) And instructions on how to actually install it. 

Here are my specs 
AMD Dual Core Processor 4200+ 2.53 GHZ 
3.00 Gigs or Ram 
80 Gigs HDD
6600 Nvidia 128 MB 

Thanks in advanced. ..

---

### Post by tzulberti on 2008-04-14
For installing Nvidia Drivers you could just go to System -> Administration -> Restricted Drivers Managers, y check the box of the Nvidia graphics card.

I you want to install from source you should first install the source of the kernel (sudo apt-cache search kernel source) and then sudo apt-get install the kernel source that you are using. After that, you must shutdown the X11 server (sudo /etc/init.d/gdm stop) from a console (F1 or F2), and then run the nvidia script.

---

### Post by regalistic2003 on 2008-04-15
> **tzulberti said:**
> For installing Nvidia Drivers you could just go to System -> Administration -> Restricted Drivers Managers, y check the box of the Nvidia graphics card.


I've tried that and everything was checked them my computer Restarted and it's still on a 800X600 Resolution Here is a Screen Shot in fact the only option i have in the drop down menu is 800X600 or 640X480 
[IMG][IMG]http://img90.imageshack.us/my.php?image=screenshotmz7.png[/IMG][/IMG]

Anything else i could do about this ? I see that you did mentioned something about Kernel Something but that really sounds like a headache, keep in mind that i absolutely don't know nothing about Ubuntu, Can you be a little more detail on steps by steps and getting this process done ? 

Thanks in Advanced/.

---

### Post by b3nw on 2008-04-15
i'm not sure this will work on 7.10 but this is what I have working on hardy (8.04):

first remove your xorg.conf file (/etc/X11/xorg.conf) then use nvidia-xconfig (as root).

this will generate you an new xorg.conf (will be for only 1 moniter)

you will then want to install a program called nvidia-settings.

use this to configure the second monitor either as a separate X session, or twinview.

hope that helps. good luck.

---

