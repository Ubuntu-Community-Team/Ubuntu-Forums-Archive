---
title: "VirtualBox 2.1 network difference between 8.04 and 8.10"
date: 2009-01-06
forum: General Help
---

### Post by eldoran on 2009-01-06
Not quite sure to begin with this one.  I'll describe the symptom:

Running 8.10 -- VirtualBox 2.1 -- I have a WinXP VM which I use to connect to a client using Cisco VPN.   I can login to Cisco and everything seems peachy -- but any communication with their internal network times out.  It almost seems like packets get sent but don't come back.

If I take the EXACT SAME Virtual machine (use the same VDI file) and run it on 8.04 with VirtualBox 2.1 -- everything works great.  

The VirtualBox configs are identical - networks are NAT.  No firewalls are running on either 8.04 or 8.10...

I guess I'm wondering where to begin diagnosis and if anyone has any ideas right off the bat?  It's preventing me from moving to 8.10 permanently and I'd love to figure it out..

Thanks for any help!!

---

### Post by eldoran on 2009-01-09
It turns out this was caused by the MTU size on my Linux host..   on 8.10 - eth0 was set to 'auto' MTU -- ifconfig showed it as 576 ..   setting it to 1500 solved the issue with the Cisco VPN client on my virtual machine.

I discovered this because 'upslug2' (utility for the NSLU2) was failing and specifically said anything but 1500 MTU would probably fail.  So after checking and fixing - I had a suspicion it might have solved some other network oddities.. sur nuf..

Anyway - in case it helps -- it appears the 'auto' negotiate of the MTU may be different on 8.10 than it was on 8.04.  Specifically setting it to 1500 may help you as it did me..  

Scott

---

