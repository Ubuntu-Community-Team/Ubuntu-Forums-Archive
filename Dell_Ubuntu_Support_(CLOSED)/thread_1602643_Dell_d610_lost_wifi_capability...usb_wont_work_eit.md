---
title: "Dell d610 lost wifi capability...usb wont work either"
date: 2010-10-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ThaKidChillz on 2010-10-21
Hey everyone,

I just recently installed ubuntu 10.10 off the site onto a Dell Latitude D610.  I was running windows xp pro before and everything worked and the FN + F2 key combination was enabling/disabling the wireless card like its supposed to.

the wlan card is a broadcom BCM4306 802.11g (rev 3) .After googling a solution, i got it to work in ubuntu for almost a week (no idea how) i installed ndiswrapper but was stumped on how to use it and just fumbled my way... so im using a wired connection right now.

Now its stopped working and it myt be because of the ubuntu update i installed although im not sure. Also, i shut down my computer last night after tinkering and trying to fix the wireless and now my usb is down. i was using a logitech mouse on it and it worked great, now it just powers up the mouse( the laser is red) but it doesnt do anything and i have to use the trackpad. 8(

Does anyone know how to address this? i really need to get these issues dealt with because this is my only computer right now.
Sugestions are more than welcome!!!

---

### Post by PRC09 on 2010-10-21
I dont know about the usb but the wireless drivers on my install were under system > admin > additional drivers.If you installed ndiswrapper I dont know what that has done but check if the b43 drivers are there and activate it and see if that will work.....

---

### Post by ThaKidChillz on 2010-10-21
I see. i went and checked the additional drivers and it says that no proprietary drivers where found on the system... i found a zip folder off another forum last night and it has that b43 that you speak of...if it is what i need, how do i enable/install it???

---

### Post by PRC09 on 2010-10-21
If you were tinkering plus playing with ndiswrapper and now other things dont work I dont know if you want to spend hours and hours troubleshooting and maybe still not get it working properly.Maybe a new clean install would work better.......I havent had the problems you are experiencing so I am sorry I cant be of much help in the troubleshooting department....

---

### Post by ThaKidChillz on 2010-10-21
i hear ya. well can u tell me how to use ndiswrapper??

---

### Post by PRC09 on 2010-10-21
You wont need to.If you have a wired connection then after the install do the updates as found in update manager and then check for additional drivers and they will be there to activate.I have a d610 and it works just fine....If you dont have a wired connection on install see the instructions in the following link.......

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by ThaKidChillz on 2010-10-23
thanks for the input man, i ended up doing a clean install of Kubuntu 10.04 and the usb problem is gone, i have the wired connection working and it says my wifi driver activated so i havnt the slightest idea what the prob could be...

---

### Post by PRC09 on 2010-10-23
So is everything working now or is wireless still a no go?

---

