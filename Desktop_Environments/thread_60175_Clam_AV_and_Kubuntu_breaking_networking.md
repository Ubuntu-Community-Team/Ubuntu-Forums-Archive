---
title: "Clam AV and Kubuntu breaking networking?"
date: 2005-08-26
forum: Desktop Environments
---

### Post by PokerFacePenguin on 2005-08-26
I have attempted to install ClamAV a few times under kubuntu and it somehow keeps breaking networking (it wont let me dhcp an ip afterwards).  I uninstall it and everything works fine.  Im no expert at using iptables, so I run GuardDog and let it do the work for me.  

Does clamav modify the iptables when it installs?  And how do I get around it if so?

---

### Post by Takis on 2005-08-26
What happens exactly? Do you try and run 'ifup eth0' (or whatever eth/wlan you're using) and that fails? Are there any error messages? Can you post the contents /etc/network/interfaces (after a ClamAV install)? Thanks.

---

### Post by PokerFacePenguin on 2005-08-26
I have it uninstalled for the moment but what happens is it wont browse internet immediately after install.  I do a quick 'ifconfig' and it reports no ip address for my ethernet interface.  Uninstalling clamav seems to correct the problem.  I have heard so much great stuff about it.  (ie..  Auto updates with freshclam).

I have a suspicion that it doesnt play well with guarddog...but thats just a hunch.  Like i said, im no guru with iptables and dont relish the prospect of manually adding all the deny and accept traffic when there is such a nice gui in guarddog to do this for me.

I'll give it another whirl at install after I complete my backup in a little while.  I just thought there may be some quick fix or maybe someone had a similiar issue with this.

---

### Post by PokerFacePenguin on 2005-08-29
I am at the end of my rope with this CLAMAV program.

EVERY time i install it.  It breaks networking....wont DHCP a thing.  Not sure if it is IPTABLES or what.  I issued a route command and it has no routes after the install.  I uninstall it and piddle with the thing and it still won't network.  

I haven't had to build my routes manually because my wifi router issues all my information to me automatically via DHCP.  

Anyone had similiar problems?

I manually added some routes...wouldnt work...rebooted again....works magically....

Im confused (again)...lol

---

### Post by Takis on 2005-08-29
Try noting your routes without Clam, and then reenter them once Clam's killed them off. Does your network work? If so, we can write a neat little script to fix your routes after Clam has started on each boot.

---

