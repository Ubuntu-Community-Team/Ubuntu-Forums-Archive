---
title: "Boot Stalls after Installation, Dell Inspiron 1100"
date: 2009-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by the_webninja on 2009-04-30
Tried to install Ubuntu 8.10 on a Dell Inspiron Laptop with 740mb of Ram, 20gb HD,
Intel Celeron 2Ghz CPU, all stock Graphics and Sound, and Internal Wireless Card was removed.
 
Installation was very slow, but completed okay. Upon Reboot sometimes the Log On Screen would pop up, sometimes nothing but Blackness. 
Re-installed several times thinking maybe it was a Bad Install but Results the same.
Changed Hard Drive to 40 Gb Toshiba, still after installation same problem.
 
I used the Boot Menu to select "Fix Broken Packages" which after returning to normal boot made the log on Screen pop up where before it would not even do that. But then after the Log on Screen you could hear a rapid couple of Thumps of the Ubuntu Start up sound then nothing but blackness. 
 
Checking the files and the Disk results came back everything "OK"
But something is not okay because the thing is not Booting. :)
 
I am thinking of Trying the New Release of Ubuntu 9.04 and see if that works.
Any Suggestions?
 
Just wanted to say Thanks to everyone who works on Ubuntu, I really appreciate this OS. Thanks!
It works fine on a couple Desk tops I have, this is the first time I have had problems installing it on a Laptop.
 
Sua*

---

### Post by WolfRage on 2009-12-10
I was reading about this model computer and it suggests that you use the alternate installation CD.
But you will need to have a standard installation disk so that you can install the boot loader to force it to install off the alternate CD, as that model has a crap BIOS. After you install the boot loader, but before you reboot swap out the standard install for the alternate installation disk. 

Reading further about your situation, you may have to flash your BIOS with the upgrade available from DELL before you can boot from a CD again.

---

