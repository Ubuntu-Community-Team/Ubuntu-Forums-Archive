---
title: "how to make wifi work after installing ubuntu 9.10 in dell vostro 1510"
date: 2009-12-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vostro1510 on 2009-12-02
i installed ubuntu 9.10 in windows xp sp3 in order to have dual boot option in my dell vostro1510. wifi card do not work when i use ubuntu.wifi starts working when i use windows........ i have Dell Wireless 1395 WLAN Mini-Card in my system
pls help me out.

how to sort out this problem:confused:

---

### Post by mikewhatever on 2009-12-02
You might be affected by the broadcom bug in Karmic. Try following this howto [http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by vostro1510 on 2009-12-02
i tried accessing internet by using a lan cable with wifi router and my system attached through it but internet is not working.........
how to connect internet........??? in ubuntu??

sry for troubling u....... again

---

### Post by mikewhatever on 2009-12-03
I don't know why ethernet didn't work, it should have. You might want to post the output of ifconfig with the cable connected.

---

### Post by vostro1510 on 2009-12-03
i used synaptic package and followed the procedure in website still it has not got activated ................

i am unable to get wifi started in my system. wired internet thing worked but still after following the above said procedure i am unable to start wifi............

---

### Post by vostro1510 on 2009-12-03
Thankyou it finally worked

---

### Post by mikewhatever on 2009-12-03
> **vostro1510 said:**
> Thankyou it finally worked

Glad it did, congratulations. For the benefit of another user having the same problem and the community at large, please sum up the steps taken to fix it. This way, we can all learn from your experience.

---

### Post by vostro1510 on 2009-12-04
i followed following steps;

First go to System, Administration, Software Sources and make sure  "Proprietary drivers for devices (restricted) is checked.

Then do this in a terminal:
     Code:
     sudo apt-get install bcmwl-kernel-source 
Reboot Ubuntu

Now go to System, Administration and "Hardware drivers" and check the  use Broadcom sta wireless driver. 

Reboot Ubuntu and you should have support for your wireless chipset.

if it does not work follow procedure in this link
_[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)_

both of these procedure works that is for sure

hope this information may also help others to get rid of this problem


               THANKYOU

---

