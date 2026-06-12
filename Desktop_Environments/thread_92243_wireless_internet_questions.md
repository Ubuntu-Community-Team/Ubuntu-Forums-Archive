---
title: "wireless internet questions"
date: 2005-11-19
forum: Desktop Environments
---

### Post by ren wins on 2005-11-19
is there a way to reset my wireless internet connection in terminal?

b/c sometimes my connection needs to be reset or repaired or something
and it'd be much easier to do it in terminal than have to restart my computer

:???:

---

### Post by Manny C on 2005-11-19
Yep. If your router is using dynamically allocating ips, then the following command should work:
```
 sudo dhclient 
```

---

### Post by ren wins on 2005-11-19
dynamically allocating IP's?

i told ubuntu the IP address that i had in windows...?
:\

---

### Post by Stambo00 on 2005-11-19
Ive had the same problems:

[http://ubuntuforums.org/showthread.php?t=90092](http://ubuntuforums.org/showthread.php?t=90092)

---

### Post by Manny C on 2005-11-19
[QUOTE=ren wins]dynamically allocating IP's?

i told ubuntu the IP address that i had in windows...?
:\[/QUOTE]
How does your router distribute IPs to the computers? DHCP or static? This can be determined by the setup of your router. You should have played with this when you first set up your router.

---

### Post by ren wins on 2005-11-20
alright
the router is dhcp, i didnt know what that meant :\ so i changed it and stuff seems a bit more stable?
we'll find out

i found that network aplet in synaptic, but i havent been able to get it to work at all...
oh well, we'll see

---

