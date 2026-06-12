---
title: "device's in kde"
date: 2005-10-14
forum: Desktop Environments
---

### Post by jimmystewpot on 2005-10-14
Hello,

I have recently upgraded to the latest kubuntu. Since upgrading when I plug in my USB memory sticks or external USB drives the hardware no longer shows up as an icon in KDE. If I goto the command prompt I can see that HAL has found the devices as per this :

12050 ?        S      0:00 [scsi_eh_4]
12051 ?        S      0:00 [usb-storage]
13483 ?        S      0:00 hald-addon-storage

However KDE does not show anything at all on the desktop. I am unsure if thats a KDE option that I cannot find or a lower level issue that I need to resolve. 

I would like to try and diagnose it but i am still learning the (k)ubuntu stuff
Any assistance would be great.

---

### Post by Knome_fan on 2005-10-14
> Breezy is also the first place to get KDE 3.4.3 which umm, should have been released yesterday. The last minute addition has caused some problems like KMail not working with GPG and media:/ not using HAL, I'll get fixes for those in -updates as soon as possible. We didn't get KOffice 1.4.2 or Amarok 1.3.3 in unfortunately, those were too close (I'm really beginning to see the advantages of gnome's 6 predictable month releases).
[http://www.kdedevelopers.org/node/1537](http://www.kdedevelopers.org/node/1537)

So, I think the short version is, they broke but will fix it shortly.

---

### Post by GeneralZod on 2005-10-14
Edit : ^^^

Whoops - too late :)

Known bug; see Knome_Fan's comment here:

[http://ubuntuforums.org/showthread.php?t=75755](http://ubuntuforums.org/showthread.php?t=75755)

Hopefully will be fixed in due course!

---

### Post by manubreizh on 2005-10-14
with upgrade to 3.5 beta1 from repos (deb [http://kubuntu.org/kde35beta1/](http://kubuntu.org/kde35beta1/) breezy main) , it seems to work now (and with some recent updates of breezy security too)

---

