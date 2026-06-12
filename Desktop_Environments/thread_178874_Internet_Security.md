---
title: "Internet Security"
date: 2006-05-18
forum: Desktop Environments
---

### Post by Geffers on 2006-05-18
I operate a small home network via a NAT router with a few IP rules set on the router's configuation options.

On my Windows machines I also run a software Firewall (ZoneAlarm) as well as a Virus Checker (AVG).

Should I be running a FireWall and Virus checker on Ubuntu and if so any suggestions as to which ones.

Geffers

---

### Post by Falados on 2006-05-18
Linux rarely has the virus problems as long as you don't run as root and do something stupid :).  Usually linux servers use antivirus to scan incoming email for windows viruses if they are a mail server.

As for firewall, iptables takes care of that.  Also Shorewall seems to be a pretty good firewall too, just have to be a little experienced with the config files.  I've found that installing Webmin and the appropriate modules lets me manage most of these advanced features through a web interface that is at least a little more user-friendly.  These can be found in synaptic (Probably need to enable the universe repositories though)

---

### Post by tallganglyguy on 2006-05-18
I've had great lucking using Firestarter. It's got a nice GUI and configuration is a snap. Takes about 30 seconds to open up the couple of ports I need and batton down the hatches otherwise. I don't worry about viruses either, I've never been affected by anything other than my own stupidity in terms of network security.

---

### Post by Geffers on 2006-05-19
[QUOTE=Geffers]I operate a small home network via a NAT router with a few IP rules set on the router's configuation options.

Should I be running a FireWall and Virus checker on Ubuntu and if so any suggestions as to which ones.

Geffers[/QUOTE]

Thanks for advice, I'll look in to suggestions.

Geffers

---

