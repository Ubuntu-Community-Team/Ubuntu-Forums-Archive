---
title: "I have a problem, well this one concerns my laptop..."
date: 2005-10-14
forum: Desktop Environments
---

### Post by jt_nept on 2005-10-14
I just installed Ubuntu 5.10 on my laptop (did I mention this is the first linux system I've ever installed?), and it goes past the boot screen just fine, but when it's time to display my monitor just shuts off.  After about a minute or two the monitor comes back on, but then the keyboard starts acting up...I'm not sure if I did something wrong during the installation, or if it is the OS itself...I'm almost certain that I completed the installation correctly.  Granted, I am new at this  :???: :smile:

---

### Post by Borusa on 2005-10-14
Hi jt_nept,

Need some more information from you :-

First of all, what laptop are you installing on?
Second, if I understand correctly, you're seeing the following ->
Normal computer start up screen...then a line that mentions 1.5, then a lot of scrolling messages with the word [OK] written next to them, then it all goes black and funny? Is that correct?

---

### Post by jt_nept on 2005-10-14
Yep, that's exactly what was happening...

**Specs:**
CPU: Mobile AMD Athlon(tm) XP2800+ 
Sound Card: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02) 
Modem: ALi Corporation Intel 537 [M5457 AC-Link Modem] 
Wireless network controller: Broadcom Corporation BCM94306 802.11g (rev 02) 
Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller 
Graphics card: ATI Technologies Inc Radeon Mobility U1 (IGP 320) 


Well, good news, I used the (sudo dpkg-reconfigure xserver-xorg) command to mess around a little.  Now I get to the login screen (command-line) and the keyboard functions fine.  Just now it says that I configured X-server incorrectly and it automatically disables it... :(

---

### Post by Borusa on 2005-10-14
That's actually not awful news. 

I don't have any experience of ATI radeon drivers, so I can't help you there. It might be useful to others if you do the following

1. Post your xorg.conf file up here, and

2. Do "startx" and post what error messages you get.

You still haven't actually said what laptop you're using, by the way :)

---

### Post by jshipley on 2005-10-14
-

---

