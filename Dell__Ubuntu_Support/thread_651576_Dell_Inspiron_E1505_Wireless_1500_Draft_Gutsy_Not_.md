---
title: "Dell Inspiron E1505 Wireless 1500 Draft Gutsy Not working HELP"
date: 2007-12-27
forum: Dell  Ubuntu Support
---

### Post by StarsEcho on 2007-12-27
Hi I'm new using ubuntu and installed Gutsy the main problem is that my wireless is not working u.u
i hope someone can help me with this thx in advance

the driver is bcm4328  

I tried with ndiswrapper but the modprobe ndiswrapper send

echo@echo2go:~/bcm43xx/DRIVER$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

wht can i do to make it work !!!?????


[and I can't get compiz to work either u.u  I installed the drivers for Ati Mobility Radeon X1300]

[Notebook details:
Dell Inspiron E1505
Core Duo 1.6
1 Gb Ram
120 Gb HD
Bluethoot (I dont know if its working but the light is on xD)
Ati X1300 128 (it only recognize 64)
Wireless 1500 Draft]

---

### Post by wormser on 2007-12-28
I have a BCM4309 and this is how I got it working.  System> Administration> Restricted Drivers Manager and go through the wizard.  I know your card is newer but its worth a shot.  I also installed my video drivers that way.

---

### Post by StarsEcho on 2007-12-28
The only restricted driver I see there is the Video driver... u,u

I might be going back to win u.u without wireless there is no point in laptop u.u

I even compile the kernel and stuff...  thats why I posted, was the last thing to do... but Thx anyway :)

---

### Post by wormser on 2007-12-28
The hardware issue is not really Ubuntu's fault.  Broadcom refuses to work with Linux and the Linux community does what it can to make it work.  But, in the end it does become a problem with Linux.  

You can get that card to work.  I saw other [posts]("http://ubuntuforums.org/search.php?searchid=33755847") where it looked like a resolution has been found.  Good Luck.

---

### Post by StarsEcho on 2007-12-29
thanks, I'm not blaming anyone, maybe some other time I'll try again :)

---

