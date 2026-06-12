---
title: "Enterprise Users - DNS Domain Name via DHCP?"
date: 2006-06-13
forum: Desktop Environments
---

### Post by somewhat on 2006-06-13
Anyone here using Ubuntu in an enterprise environment?  I've noticed when testing Ubuntu at work in our Windows AD environment that when an Ubuntu client picks up DHCP from our Windows DHCP server, it will not receive our DNS Domain Name.

If you look in the address leases in the DHCP MMC, all you see is a blank name.  On the client it also means I have to use FQDNs when connecting to Windows resources in our domain as the local search suffix is not ammended. (I know I could add this manually, but..... ;) )

I've noticed that other distros I've tried at work do not have this prob, SUSE, Fedora et al all receive the DNS Domain name via DHCP.  In good taste I did search the forum first and found [this]("http://ubuntuforums.org/showthread.php?t=47444&highlight=dns+suffix+dhcp") old post in the Hoary Forums which got no replies.

Surely with the enterprise ready message of this release others are actually using Ubuntu at work and are finding this a problem?  Can anyone else shed light on this/confirm if they experience different behaviour?

---

### Post by somewhat on 2006-06-13
heh ahem errm ok well ignore most of that - it seems actually it does ammend the search suffix to my /etc/resolv.conf and I can ping via hostname and it will search the our domain.

I guess my query now is why does name show as blank in DHCP?  It seems only Ubuntu does this so far, and when makes for curious entries when one is reconciling DHCP leases.  Is there something non standard about Ubuntu's replies to DHCP servers?  

Will have a looksee with Ethereal soon

---

