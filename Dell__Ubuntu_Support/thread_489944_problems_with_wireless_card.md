---
title: "problems with wireless card"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by steffey02 on 2007-07-01
I just changed from windows xp to ubuntu. i have a dell 1505 with a dell wireless 1390 wlan mini-pci card. it does not recognize the wireless card. how do i make it compatible.  any help would be greatly appreciated.

---

### Post by neptho on 2007-07-02
Try following the [information in this blog entry](http://pervasivecomputing.net/ubuntu_feisty_7_04_on_dell_inspiron_e1505) to get your 1390 to work, and let us know if you have any problems.  As I don't have a 1390, I'm not sure which driver to download from Dell's site, but you should be able to download the .EXE and unzip it by renaming it to .zip.

---

### Post by Unicast on 2007-07-02
I'd highly recommend using the latest version of ndiswrapper(1.47) and [this driver](http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R151517&SystemID=INSPIRONI6400/E1505&servicetag=&os=WW1&osl=en&deviceid=9805&devlib=0&typecnt=0&vercnt=9&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136) from Dell.

More info here: [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

But use the driver version above and ndiswrapper 1.47

---

### Post by James.Dedon on 2007-07-02
All I had to do was run the bcm43xx fw-cutter and my dell wireless card worked just fine.  I never had to mess with ndiswrapper or the rest of that stuff.  Supposedly the firmware and drivers are included in the distro, but the fwcutter is needed because they are proprietary.

---

### Post by steffey02 on 2007-07-02
> **Unicast said:**
> I'd highly recommend using the latest version of ndiswrapper(1.47) and [this driver](http://support.euro.dell.com/support/downloads/download.aspx?c=uk&l=en&s=gen&releaseid=R151517&SystemID=INSPIRONI6400/E1505&servicetag=&os=WW1&osl=en&deviceid=9805&devlib=0&typecnt=0&vercnt=9&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=202136) from Dell.

More info here: [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

But use the driver version above and ndiswrapper 1.47

i used the method you said above but the terminal says ndiswrapper is not installed but when i search the filesystem theres a lot of ndis files there and i cant delete them it just says acces denied. ive tried the nautilus command in the tut but had same effect. in the terminal i am here:
root@stephanie-laptop:/home/stephanie#
can any1 help from here?

---

### Post by Unicast on 2007-07-02
When you search for ndiswrapper how many items do you find?

With version 1.47 installed I find 15 items when I search for "ndiswrapper"

See the attachment below:

---

### Post by steffey02 on 2007-07-02
i find 10 items.

---

### Post by Unicast on 2007-07-02
Ok.....

Alt-F2  (Hold Alt and press F2)

Enter** gksudo nautilus** in the window that appears and click on **Run**

Enter your admin password.

Double click on **File System** on LHS of Nautilus window, then click on the search button and type ndiswrapper and hit enter.

Then delete all instances of ndiswrapper that nautilus finds. Please be careful here, you can delete stuff here and do lots of damage to Ubuntu if you're not careful!!

Then try the tutorial.

---

### Post by steffey02 on 2007-07-05
Thanks to everyone for all of your help. I finally have my wifi card up and running, thanks to paperdiesel's HOW TO: Dell Inspiron E1505 Wireless (Broadcom 1390 WLAN):D

---

