---
title: "wireless internet connection sharing from wired ubuntu laptop to wireless xp laptop"
date: 2006-02-27
forum: Desktop Environments
---

### Post by VCSkier on 2006-02-27
i guess the title says most of it.  i'm runing breezy on my laptop in my dorm room, and i leave it on and plugged into my ethernet port alot.  i'd like to create a wifi network to share my wired connection, so anyone in range w/ a wireless card can access the internet.  i'm not interested in any encryption or anything for the time being, maybe later if too many people are draining my bandwidth, but not at first.  a friend of mine can set this up really easily in tiger osx...  so it should be easy, and even better w/ ubuntu, right?  :cool:

edit:  btw, i'm currently using NetworkManager Applet 0.4.1 to manage *my* connection.

---

### Post by RAOF on 2006-02-27
Well, what you want to do is really in two parts:  you'd need to set up your Ubuntu box as a DHCP server, listening on your wireless card, and you'd need to set up a NAT firewall-type-thing to forward the relevant packets to the wlan.

Browsing a forum search on "internet sharing", it seems that the "firestarter" firewall/nat configuration tool can be used to do what you want.  Give it a whirl - sudo aptitude install firestarter

---

