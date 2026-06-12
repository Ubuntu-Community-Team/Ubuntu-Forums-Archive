---
title: "Avant-Window-Navigator not function"
date: 2008-04-03
forum: Desktop Effects &amp; Customization
---

### Post by ketoophat on 2008-04-03
Hi, I'm newbie in ubuntu. Just a few month migrate from windows to Ubuntu. My problem is about AWN.

I'm using Gusty Gibbon 7.10, i have completed install AWN, but when i want running AWN (using Application - Accessories - AWN), the window just appear one second and then disappear. I tried run using terminal, but the error message occured 

zazyma@zazyma-mebius:~$ avant-window-navigator &
[1] 7059
zazyma@zazyma-mebius:~$ /home/zazyma/.themes/imetal-grey-simple/gtk-2.0/gtkrc:58: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/zazyma/.themes/imetal-grey-simple/gtk-2.0/gtkrc:59: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/zazyma/.themes/imetal-grey-simple/gtk-2.0/gtkrc:60: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/zazyma/.themes/imetal-grey-simple/gtk-2.0/gtkrc:61: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

I don't know how to solve it. Please help me if possible. I'm using Notebook Sharp Mebius. The graphic card is :

zazyma@zazyma-mebius:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: S3 Inc. VT8375 [ProSavage8 KM266/KL266] [5333:8d04]

thank for any help.

---

### Post by Seisen on 2008-04-03
Are you running compiz or another compositing manager?

---

### Post by rahimveron on 2008-04-03
It needs compiz running to work.

---

### Post by ketoophat on 2008-04-03
i've finished install compizfusion, but i don't know wheather is correct or not. I just follow the guide when install compizfusion. In the terminal when enter compiz--replace the error message occured

zazyma@zazyma-mebius:~$ compiz --replace 
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

