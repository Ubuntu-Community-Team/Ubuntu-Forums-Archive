---
title: "internet access on Kubuntu"
date: 2009-03-26
forum: Desktop Environments
---

### Post by pgmuthukumar on 2009-03-26
Hi,
I have recently installed KDE/Kubuntu along with Ubuntu 8.10.  I dont have any idea on how to connect to internet.  Because the internet is working in Gnome and windows XP but not in Kubuntu.  
Please help.

Thanks,

---

### Post by pgmuthukumar on 2009-03-26
Hi,
Even I have tried KNetworkManager but the right click on the icon is not working.  Also, tried the steps mentioned in the page
[http://yunos12.blogspot.com/2007/07/ubuntu-how-to-connect-to-internet-using.html](http://yunos12.blogspot.com/2007/07/ubuntu-how-to-connect-to-internet-using.html).  Still no luck :|.

Any idea...?

Thanks

---

### Post by freeman2000 on 2009-05-14
any ideas out there ???

---

### Post by tacantara on 2009-05-14
I had the same problem when I added the KDE package to my existing Ubuntu system.  By enabling the Network Manager applet on the taskbar, I was able to get into the manager and enable wi-fi. Have you installed that applet yet?  Check out the thread below, from when I was seeking the same info that you're looking for now.  Hopefully this will solve your wi-fi issue :KS

[http://ubuntuforums.org/showthread.php?t=1141503](http://ubuntuforums.org/showthread.php?t=1141503)

---

### Post by rudie_techie on 2009-05-14
In terminal run : ```
pppoeconf
``` Create a connection and then in terminal again type ```
pon
``` to connect and type ```
poff
``` to disconnect from the internet. Hope this helps!

---

