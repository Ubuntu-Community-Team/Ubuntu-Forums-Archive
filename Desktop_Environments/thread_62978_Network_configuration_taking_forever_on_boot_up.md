---
title: "Network configuration taking forever on boot up"
date: 2005-09-06
forum: Desktop Environments
---

### Post by dsbeav on 2005-09-06
I'm running a gateway 74xx series computer amd64 processor etc etc...
I'm using NDISWRAPPER and 64 bit broadcom drivers to run my wireless card.

Ok, here's the problem.  During bootup, my computer goes through the processes very quickly untill it comes to network configuration.  It normally sits here for about a minute and a half, then proceeds.  The rest of my boot process takes all of about 15 seconds.  

In /etc/network/interfaces i turned off all the auto wlan0, and auto eth0 stuff on bootup.  Still slow.

Is there anything, I could be missing or anything i could do to speed up the process?

Thanks!

---

### Post by mr_mop on 2005-09-06
Are you using DHCP? My machine seems to take ages too with DHCP.  I sort of fixed it with a fixed IP but its not so useful with a fixed IP.

---

### Post by dsbeav on 2005-09-07
Yeah I'm using DHCP.. I have wireless internet and also no static IP.  Is there anyway I can prevent it from going through all that on bootup and just do it manually when I need it once in Linux?


Thanks!

---

### Post by mlomker on 2005-09-07
[QUOTE=dsbeav]Yeah I'm using DHCP.. I have wireless internet and also no static IP.  Is there anyway I can prevent it from going through all that on bootup and just do it manually when I need it once in Linux?
[/QUOTE]

Is an interface listed with ifconfig after you get into your desktop?  If so, then hotplug is bringing up the interface and if it can be seen by ifconfig then it'll cause the delay.  There are a lot of generic how-to's on the Internet giving many strategies for profiles and custom scripts, etc.  You can spend a lot of time monkeying around...I've spent a day, myself.  In the end I decided that the brief delay when my ethernet is unplugged is easier to deal with than the complexity of changing things around.

---

### Post by dsbeav on 2005-09-08
[QUOTE=mlomker]Is an interface listed with ifconfig after you get into your desktop?  If so, then hotplug is bringing up the interface and if it can be seen by ifconfig then it'll cause the delay.  There are a lot of generic how-to's on the Internet giving many strategies for profiles and custom scripts, etc.  You can spend a lot of time monkeying around...I've spent a day, myself.  In the end I decided that the brief delay when my ethernet is unplugged is easier to deal with than the complexity of changing things around.[/QUOTE]


You're probally right...
Thanks for the help!

---

### Post by briguy on 2005-09-09
I have a Gateway 200x which had the same problem.  This solved it painlessly for me: [http://www.ubuntuforums.org/showthread.php?t=31198&highlight=network+boot+slow](http://www.ubuntuforums.org/showthread.php?t=31198&highlight=network+boot+slow)

---

