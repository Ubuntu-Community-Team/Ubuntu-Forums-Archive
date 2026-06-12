---
title: "Edubuntu gutsy issues: Any ideas?"
date: 2007-11-10
forum: Education &amp; Science
---

### Post by kesomir on 2007-11-10
I trialled gutsy on a sngle machine until last week (school holidays) when I rolled out to the whole network (minus my NFS / openLDAP / Web server which was left on feisty). Here are my experiences:

On Monday Under full load, the NFS server was brought to a crawl. This didn't happen with the clients accessing it running feisty.

I migrated the NFS role to a new (more powerful) server running gutsy as a basic server install with NFS server and quota installed. This Kernel panicked once a day from Tuesday to Friday when it started to kernel panic at an increased rate.

I replaced the gutsy server with Debian 4 - yesterday (Friday), it hasn't run under heavy load so can't comment on it yet.

Another box (Edubutntu LTSP server) upgraded to gutsy displayed an issue with run away processes (tux type in one instance). This caused the box top quickly reach 100% utilisation on both cores and effectively die (uptime load score of over 40 ;) ) . Restarting the box dropped load to ~3.

So......

What do you recommend? : Roll back to Feisty? Persevere and see what the network is like under load on Monday?

I have already swapped ubuntu for debian on the NFS server, but need to wait to see how it performs. (Two exports - home and a single export containing shared folders on NFS3).

I also have an issue where clients sometimes fail to mount NFS folders on startup (ssh'ing into them and mounting the folders fixes this) but that also occurred under feisty.

Any comments and help appreciated.

---

### Post by LaserJock on 2007-11-10
I would email the edubuntu-users mailing list (you can find it on [http://lists.ubuntu.com]("http://lists.ubuntu.com") ) describing your problem. You might actually want to search around in the archives of the list because there are lots of good tips on server usage optimization and process cleanup.

-LaserJock

---

