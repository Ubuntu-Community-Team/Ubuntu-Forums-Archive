---
title: "New User - Can't Connect - HELP"
date: 2006-03-01
forum: Desktop Environments
---

### Post by deniro0311 on 2006-03-01
I will try not to get too long winded.  After a very long distro shuffle, to include Kubuntu, I have settled with Ubuntu.  I hate Gnome, but Ubuntu seems like a great distro for my client-side computers.  It is fairly quick, not buggy, has a promising future, and has the BEST community hands down.  Here is my problem, which I have only faced with Ubuntu and Kubuntu.  I simply can not connect to the internet.  I can use synaptic, but I can't use my browser.  I can ping myself, but I can't ping any other computer, internal or external, so it isn't a DNS issue.  I am running behind an IPcop router/firewall.  This is not the issue, because I can connect with Windows (which is on another drive) and various live CDs.  When I try dhcp it tells me the host is not reachable.  When I try static it just sits there trying to connect.  Maybe it is my drivers.  I have an nForce4 chipset with dual gigabit ethernet.  It has an nvidia ethernet controller and a marvell yukon ethernet control.  I have gone through all the config files to make sure everything is set correctly.  Does Ubuntu have some weird way it likes things setup?  I have also been reading that ipv6 can cause problems.  At this point I am completely lost.  I am very close to going back to my backup distro, but I really would like to stick with Ubuntu.  Any help would be much appreciated.

---

### Post by andrewsawyer on 2006-03-02
Can I confirm something you said - you CAN connect to the internet through Synaptic, however you CAN'T ping say [http://google.com?](http://google.com?)

---

### Post by uber_drizunk on 2006-03-03
Can you confirm you can ping internal and/or external machines from windows?
maybe ICMP (ping) is blocked on the firewall. Also if synaptic is able to download packages from internet then your LAN connection is fine and so is access to internet.

are you using any proxy for internet in your browser?

---

