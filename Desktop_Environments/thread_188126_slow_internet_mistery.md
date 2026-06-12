---
title: "slow internet mistery"
date: 2006-06-03
forum: Desktop Environments
---

### Post by enrivar on 2006-06-03
I have three PCs (1 desktop and 2 laptops) connected to the Internet by a linux proxy. desktop pc runs kubuntu Breezy and the 2 laptops run Dapper. I'm experiencing a strange behaviour of laptops. Local networking works as it should (100 Mbps) but downloading from internet is painful (20Kb/s of the 600Kb/s available). DNS resolution is not the problem, it's quite fast (as the breezy machine). All 3 PCs have a realtek 3819 chipset on their nic (same module loaded). Tried to disable ipv6 (in /etc/modprobe.d/aliases set alias net-pf-10 ipv6 off, net-pf-10 off and ipv6 off) but with no luck. 
Additional notes:
- one of the laptop was running debian till yesterday with no problems
- the other laptop works if I first boot into windows and than soft-reboot back into linux (also for this pc there was no issue with previous versions of Kubuntu)

any hint will be highly appreciated,
enrico

---

### Post by GeLeTo on 2006-06-05
I have the same problem.
On my dual-booting machine under ubuntu the speed is >10 times slower than on WindowsXP.
I disabled IPV6 and it didn't help (in /etc/modprobe.d/aliases , also renamed ipv6.ko just in case)
The nic is Realtek 8029 based.

---

### Post by bbrg548 on 2006-06-05
I am having a similar problem. Every internet function seems slow. The problem is not limited to Firefox (1.5.0.4), as I have noticed it with RealPlayer also. I added FasterFox, which seemed to help only a little, and only in FF (of course).
It does not seem related to my router, as I have the same problem at home and at the rescue station.

It started when I upgraded to Dapper(6.06). No other changes to my system were made.

The problem seems to be mainly with DNS lookup, but also effects download speed intermittently.
DNS lookup seems to be faster for sites I have visited in the same browser session, but this can be erratic.

Any ideas?

---

### Post by cyberb0b on 2006-06-05
/etc/resolv.conf

This file is your friend.  Remove invalid lines of text (like 192.168.0.1) and verify with your ISP that the correct DNS servers are listed.

---

