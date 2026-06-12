---
title: "Random Ethernet Connection"
date: 2009-02-12
forum: General Help
---

### Post by AbsentHarvest on 2009-02-12
The majority of the time, I have no issues.  Other times I need to reboot, reboot again or even a third time to have my internet working.  Anyone?

---

### Post by digitalbenji on 2009-02-12
is this a laptop or desktop?  When this happens, you should do dmesg to see what's going on.  It could be that the DHCP lease is expiring, which can be resolved by doing ```
sudo /etc/init.d/networking restart
```  You can also try ```
sudo dhclient eth0
``` if the problem is DHCP.  Please provide more information to help us help you.  

Thanks,

---

### Post by AbsentHarvest on 2009-02-12
Thanks for replying so quickly.
This is a desktop computer.  Inspiron 530 (Custom Build)
It started to occur after I did updates.  Or atleast that's when I noticed it.

I do my thing, and once I restart it... It won't connect.. I have to restart a couple of times to get the connection back.  Which you can imagine is quite inconvenient.  I'm trying to make this my main operating system which is why I need the internet to work properly (all the time)

What I thought before I made this post was perhaps there is a IP or DHCP problem but I have no idea how to check for that kind of thing on this operating system.  Linux is a whole new world for me so any help is greatly appreciated.

---

