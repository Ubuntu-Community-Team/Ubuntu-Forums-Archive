---
title: "ANY IDEA?? - Internet"
date: 2005-12-23
forum: Desktop Environments
---

### Post by ESPOiG on 2005-12-23
wen i want to goto say ubuntulinux.org or ubuntuforums.org or gnome.com or wateva it is and other sites like proper developed ones for sum reason, firefox and any other browser i use... just sits

it doesnt load the page and then after a while it says page not accessible

while this is happenin im in windows browsin the same site no probs... and i have a 1.5mg dsl connection and the comp with linux (ubuntu) on it also has windows, and wen i use that and browse these sites they are fine... and with the same browser aswell

i havent a clue wat it is but i wuld like to be able to browse the net as well

*note google runs fine for pics and normal searches

---

### Post by syklitengutt on 2005-12-23
have you configured your connection proporlie?

---

### Post by fordfan753 on 2005-12-23
Is it just web browsing that doesn't work or all internet related stuff?

---

### Post by ESPOiG on 2005-12-23
i dunno i dont use much other internet stuff... maybe gaim once in a while and i dunno how im supposed to configure the internet cuz it always used to work... and it is dsl 1.5mb over lan through a router

---

### Post by fordfan753 on 2005-12-23
It could be a couple of things, either your network settings aren't configured properly, or you need to turn the IPv6 tunnelling thing off in firefox, it's most likely the settings though.

---

### Post by ESPOiG on 2005-12-23
how do i do that :D... im stupid both the firefox thing and how to get to setting :D... im new to linux

---

### Post by fordfan753 on 2005-12-23
The firefox setting can be changed by opening firefox and typing "about:config" in the address bar, hit enter. Type "ipv6" in the filter bar and turn network.dns.disableIPv6 to on. I don't think this is likely to be the problem, but it's worth a try.

As for network settings do you know your router or modem ip address?

---

### Post by ESPOiG on 2005-12-23
yeh it was that ipv6 thingo thx alot :D

---

### Post by cwaldbieser on 2005-12-23
[QUOTE=ESPOiG]how do i do that :D... im stupid both the firefox thing and how to get to setting :D... im new to linux[/QUOTE]
If you skip down to the bottom of this link:
[http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643")
It will show you how do disable IPv6.  Also, in Firefox, you can enter "about: config" in the URL and search for IPv6.  Toggle it off.

---

