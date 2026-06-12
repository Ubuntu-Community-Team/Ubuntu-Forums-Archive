---
title: "No network detected Centos 3.5 &amp; 4"
date: 2008-02-21
forum: Fedora/RedHat and derivatives
---

### Post by jseiser on 2008-02-21
I'm installing a server with centos on it for our Voip systems.  I install centos as normal, the motherboard is a giabyte GA-945GCMX-S2

I cant get the network to work at all.  I tried another version of the motherboard, thinking it was a bad nic, since the traffic light and power light were both on constant.  Same issue.  Installs fine, everything works, I just cant do anything internet related, mainly, update my system.  Could this be an issue of 3.5 and 4 being to old for this hardware?  its not top of the line or anything.  Is this a centos/redhat issue?  Im wondering if i should try debian on it.  I cant see the hardware recognition being better in debian than redhat, or am i wrong?

Ive tried ifdown eth0
ifup eth0

i tried, using netconfig
i tried restarting the network

This isnt like arch, where i would go to the rc.conf and tell it dhcp, update, then edit that same file for static.  Ive googled around, but nothing with this Mboard comes up as being bad with linux etc.  Any ideas?

---

### Post by steeleyuk on 2008-02-22
You could always try CentOS 5.1. There's a Live CD version of it too so you can check whether it detects it or not.

---

### Post by jseiser on 2008-02-22
Thanks, its actually what i had to do.  For some reason it was seeing the LAN as a different chipset then it was.  The wrong version i guess, and when i would try to install the module, i was told the kernel doesnt support modules and to recompile the kernel.  lol, no thanks :)

---

