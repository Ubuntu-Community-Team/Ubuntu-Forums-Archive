---
title: "AIT Readon Compiz problem"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by syperus on 2007-10-08
Hello, I had compiz fusion working perfectly, but i could tell the graphics were slightly off, slower system, ect...I decided to update my graphics card to see if it helped..Well it did..my system is faster now, but now compiz fusion does not work. I can't even enable desktop effects. I read a post somewhere on here that if you use a ATI readon card then you need to do alot of customizing. I couldn't find any tutorials on this so i was wondering if anyone knew of any or how to customize it to get it to work?? I have a ATI readon 9700.  Thanks

---

### Post by Forlong on 2007-10-08
What graphics card did you use before and what driver do you use now?

---

### Post by syperus on 2007-10-08
i always had ATI readon graphics card. Didn't change the graphics card, just updated the driver..i downloaded the Linux x86 -> Readon -> 9700 series from [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)  since it says i have 9500 pro / 9700 graphics card

---

### Post by vav on 2007-10-08
For the ATI cards, there are two drivers available. If you go to the restricted drivers manager, in System->Adminstration it'll show you that an fglrx driver is available. Try using that. If that doesnt work, try disabling that so that the standard xserver-xorg-video-ati open source driver is used.

The ati driver worked for me, while the fglrx driver worked for a friend. It's a hit and miss situation as I see it.

---

### Post by syperus on 2007-10-08
what if i don't have that option in my System -> Adminstration section?? only options i have in there is Keyring Manager, Network Tools, Printing, System Log, System Monitor, Update  Manager, Windows Wireless Drivers. Thats all i have there.

---

### Post by Forlong on 2007-10-08
> **syperus said:**
> Didn't change the graphics card, just updated the driver
Ah OK, then you need [Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl) now.

---

