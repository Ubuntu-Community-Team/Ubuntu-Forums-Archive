---
title: "General question about update procedures"
date: 2005-05-01
forum: Desktop Environments
---

### Post by faddat on 2005-05-01
Shortly I will be attempting to build a desktop environment based on Ubuntu that will hopefully be able to scale easily.  Initally, I would expect to have about 50 users, and from there, there should be lots and lots of users.

/home should be stored on our servers, while the rest of the computers are connected to our servers by a 1-30 Megabit connection.  In the part of the world we're in, access to the internet is a bit rough, so we'd like to pull in package updates to our server, and distribute them over our network.  I'm curious what the schedule/formalized plans for package updates are with Ubuntu.  I was using Kubuntu Preview previous to the release of the final, and of course, there were many more (often daily) package updates than with the final.  Is there a timetable or a policy for when and how package updates are made to the finals?

Also, I've heard rumors of an Xubuntu (XCFE+Ubuntu) going around.  That would be quite ideal for our situation.  Is there a plan to create a separate ISO, or would it seem like the general flow is toward just using the packages?

What are network installs like?  Could we customize .iso so that upon inserting the CD and getting on our network, the CD could find our package servers?  It would be nice to be able to centrally distribute packages for flash, java, etc.  

And yet another question.... anyone got any ideas on reliably implementing OO.o 2.0?  Right now I can't take 1.0 off of my Kubuntu system because it seems to be a part of the Kdesktop metapackage.  

What sort of administration tools are available for ubuntu?  Is there one that would make a standardized user list/set of packages possible?  We'd like to have each PC on our network identical in terms of software, so that any user could log in to any PC on our network, and have access to their /home folder.  

Finally, could anyone point me to a good administration suite for Internet cafes?  We'll probably be working with many of them, and we'd need to be able to track usage by the individual cafes, and then on the network as a whole.  

We'll be working with older computers in West Africa, so if you have any thoughts on that specifically, please let me know.

---

### Post by jamez on 2005-05-03
You'll want to store all of your users' /home directories on a NFS server. This server will need lots of disk space and an external backup solution of some kind (tape, external hard drive, whatever fits your budget). You might also want to consider using autofs on the clients when mounting /home directories, so as not to bog-down the NFS server from too many static mounts. 

You'll also need a caching proxy server. This server will need 2 hard drives: 1 for the OS, the other for the squid cache (for optimum performance), and lots of RAM (preferrably 1 GB). The purpose of having a caching proxy is two-fold: to act as a firewall (so long as you don't allow external gateway access from the clients), and to cache all downloads to disk so the next user can grab his updates/downloads/packages/whatever directly from the proxy server disk cache, without going out over the internet (saving bandwidth). The configuration parameter you want to pay attention to when caching large amounts of web data is "max_object_size". Set this value up as high as the largest downloadable filesize you think your users will encounter (entire isos even, if you have the disk space).

Then there is the problem with managing your users. WIth 50  users, you can probably get away with managing them without directory services (manually creating users and home directory mount points on the NFS /home server), but once you get to 100+ users, you might want to consider a NIS/ldap set-up (beyond the scope of this post).

This is obviously the tip of the iceberg, but I'm sure there are others out there with more extensive experience in large-user environments who can contribute.

BW: I'm also interested in a Linux-based Internet Cafe solution...something along the lines of IPCop-inspired solution. Anyone with suggestions?

---

