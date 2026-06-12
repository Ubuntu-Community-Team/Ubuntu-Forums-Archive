---
title: "Help! Dapper hangs on boot while &quot;Starting portmap daemon&quot; (even in single-user mode)"
date: 2006-07-27
forum: Desktop Environments
---

### Post by temcat on 2006-07-27
Hi all,

seems like I have b0rked something. I installed KDE via Synaptic using kubuntu-desktop metapackage, and then I removed vmware-server to free some place on the hard disk. Now Dapper consistently hangs on boot while "Starting portmap daemon" with various kernels (2.6.15-23/26-386/686) and even in single-user mode.

How do I repair it?

Update 1: I have found a mention of a possible cause, namely that the loopback interface is not brought up until after the portmap daemon is started. This is not of much help however, since I do not know how to fix that. Any ideas?

Update 2: I chrooted into Dapper from Edgy partition and removed portmap package altogether. Now the boot process hangs on configuring network interfaces.

Here's my /etc/network/interfaces file:

auto lo
iface lo inet loopback

iface ppp0 inet ppp
provider ppp0

auto ppp0

In logs under /var/logs I cannot find anything relevant.

---

### Post by temcat on 2006-07-27
-- updates moved to the parent post --

---

