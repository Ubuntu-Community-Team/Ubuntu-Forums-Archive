---
title: "Dell Mini 9 and Vodafone"
date: 2009-03-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by figi22 on 2009-03-31
I'm thinking about getting a Dell Mini 9 and Vodafone, but not sure how to go about it...

I can get a Dell Mini 9 with Windows XP (yuk) and Vodafone for £20/month.   But it will look and feel horrible.

I can buy a Dell Mini 9 with reasonable spec and Ubuntu for £250ish, but I will need to spend £15/month on a Vodafone dongle/USB stick.   It would still make me feel better, but I need to know that it would work.

I've seen various bits and pieces suggesting that it's easy to get Huawei E172 working but maybe not Huawei E220?   

Does anyone have some definitive info on Dell Mini 9 and Vodafone broadband?

Also, my travelling route wouldn't be fully 3G, mostly 2G, so does any of this make any difference?  What should I concentrate on???

Thanks,

Fiona.

---

### Post by armandh on 2009-03-31
since the mini 9 works well with OOTB 8.10, if any usb accessory works with 8.10 on a desktop I see no reason why it would not work on a mini9 running 8.10.

but I have NOT tried it.

---

### Post by figi22 on 2009-03-31
OK - thanks.   I think I need to try this before shelling out... maybe I can borrow my mother's Dell Studio which runs 8.10 and try it out in a Vodafone shop.

Only other thing... how do I load 8.10 on a Netbook if I have no CD drive?   They ship with 8.04 - can you just upgrade directly via the net?

---

### Post by anjilslaire on 2009-03-31
YOu can put Ubuntu 8.10 onto a usb flash drive via 8.10 by using the included "Create a usb startup disk" tool.
1. Download the 8.10 ISO on your mom's studio
2. insert a usb flash drive, 1gig will work.
3. Run the Create a usb startup disk" from the system menu, point it to the ISO as the source, and your usb drive as the destination.
4. You now have a bootable Ubuntu 8.10 installer on a usb drive. 

Plug it into your mini 9, boot the system and install. Some great guides are available here:
[http://www.ubuntumini.com/2008/10/user-guides-for-ubuntu-810-intrpid-ibex.html](http://www.ubuntumini.com/2008/10/user-guides-for-ubuntu-810-intrpid-ibex.html)

---

### Post by figi22 on 2009-04-01
Brilliant!  Thanks!

---

### Post by ugm6hr on 2009-04-03
There are plenty of reports regarding the E220 and Linux / Ubuntu.

This is one: [https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220)

Look at Gnome-PPP for GUI configuration:
[https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220/GnomePpp](https://help.ubuntu.com/community/DialupModemHowto/Huawei/E220/GnomePpp)

Good luck.

---

### Post by shof2k on 2009-04-08
Am running a mini9 with a vodafone pay as you go broadband dongle (K3565).  Ubuntu recognised the dongle, but I had to change the connection parm before it finally worked.

Word of warning, although the broadband works on ubuntu,the vodafone software isn't ported yet.  Therefore you'll need a windows machine to top up.

---

### Post by craptree on 2009-08-30
Works perfectly under jaunty after some updating!

see [http://ubuntuforums.org/showthread.php?t=961334&highlight=vodafone+dell+mini](http://ubuntuforums.org/showthread.php?t=961334&highlight=vodafone+dell+mini)

Riz

---

