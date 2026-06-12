---
title: "Dell Inspiron 1520 wifi troubles"
date: 2008-01-22
forum: Dell  Ubuntu Support
---

### Post by dougbe on 2008-01-22
I'm having trouble getting my wireless card to work in Ubuntu. I just recently ordered a Dell Inspiron 1520 laptop with Windows XP and set it up to dual-boot with Ubuntu. Here are my stats:

Dell Inspiron 1520 Laptop
Ubuntu 7.10
Dell 1505 Wireless-N Mini-card

I think I've managed to get the drivers installed using ndiswrapper, but when I click on my network manager no wireless networks show up. 

If I go to System -> Admin -> Windows Wireless Drivers, in the installed drivers window I see: bcmwl6; hardware present: yes.

But when I click on network manager the only options are Wired Connection, or Manual Configuration. If I boot into windows the wireless works fine, so I know there is wireless available here.

Any help would be greatly appreciated. I've been searching the forums for quite some time now and can't seem to get this working.

---

### Post by ankuryu on 2008-01-22
Hi , 
   I too have the same problem.  However My Dell Latitude D520 with Kubuntu Fiesty Fawn, used to have wireless options in the Network Manager however it just vanished one Day and since then I am searching for the solution.

   However I followed this thread
   [http://ubuntuforums.org/showthread.php?t=318539]("http://ubuntuforums.org/showthread.php?t=318539")
   and am able to connect to a WPA2 encrypted WiFi.  You can check it out if you would like to.  I shall share the solution when I find one

Till then Best of Luck

Bye

---

### Post by dougbe on 2008-01-22
Somehow I always end up answering my own questions shortly after asking for help.

It seems as though the driver I had installed was actually the wrong driver, even though it installed in Windows Network Drivers and detected the hardware. I think I had selected a driver for the US when I reside outside the US. I think my second problem was that I was copying the .inf file of the correct driver to the desktop before trying to install it. When I put the .inf file back in its original folder (with the corresponding .sys file and everything else) it installed okay. After installing the correct driver I rebooted and my wireless connections were available.

---

