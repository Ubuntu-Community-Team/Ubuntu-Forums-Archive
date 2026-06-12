---
title: "First experiences of Kubuntu after years of Mandriva"
date: 2005-08-30
forum: Desktop Environments
---

### Post by beewer on 2005-08-30
I installed Kubuntu yesterday. Installation went quite ok. KDE is pretty, bootup time is less than in Mandriva and system feels bit more responsive than Mandriva LE.

And apt-get rocks! 

But I had few minor problems:
1. dual head display
I have two monitors and two graphics cards: geforce 256 and old s3. In Mandriva LE dualhead was installed automatically but in Kubuntu it wasn't. I fought couple of hours trying to get it working with no success.

2. Setting of static ip
I need a static ip. I tried to manually edit ifconfig and resolv.conf: no success. I tried to set static ip from KDE's Control Center: no success.
Finally I gave up and configured my router to give always same ip address according MAC address.

What I miss from Mandriva is all those little GUI tools that help configuring system. But I switched because I want a system which doesn't need clean install more than once. I wait eagerly to see how upgrade goes from 5.04 to 5.10.

---

### Post by heimo on 2005-08-30
I can probably help only on the second question - for the first one I can only give you this link:
[https://wiki.ubuntu.com/XineramaMultipleMonitors](https://wiki.ubuntu.com/XineramaMultipleMonitors)

I've seen dualhead system questions discussed on these forums - so you should probably search what others have done.

For static ip, if GUI for some reason doesn't work, you can edit /etc/network/interfaces. It's quite easy to edit (see man interfaces for syntax). Something like this should do:
 ```
auto eth0
iface eth0 inet static
   address 192.168.0.2
   netmask 255.255.255.0 
   gateway 192.168.0.1

``` 

DNS-servers go to /etc/resolv.conf

This may be helpful
[http://www.ubuntuforums.org/showthread.php?t=25557](http://www.ubuntuforums.org/showthread.php?t=25557)

---

