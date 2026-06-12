---
title: "Spanned disk volume"
date: 2009-06-17
forum: General Help
---

### Post by Javijavi on 2009-06-17
I am trying to set up a general purpose file server for my LAN using Ubuntu 9.04. I have set up a workstation with 4 harddrives installed. The first drive is the OS drive and the other 3 will act as pure file storage. Under windows I was able to use the disk management utility to format these drives as "dynamic disks" in a spanned fashion so that all of their storage space was combined into one logical unit. For instance, each drive is 400GB, when spanned together windows treated it as a single drive totaling 1.2TB. 

Is there a method to do the same in ubuntu? 

And I hate to derail my own thread, but regarding file server capabilities of ubuntu, does the ubunto 9.04 iso I downloaded from the ubuntu hompage already come with samba available and ready to use? I havent been able to find anything related to setting up a windows compatable network file server with ubuntu yet.

---

### Post by grantemsley on 2009-06-17
For spanning disks, look at LVM. Search for LVM here or on google and you'll find plenty of guides.

For file server, you need to install samba.  Just go into the package manager and search for it (or open a terminal and type "sudo apt-get install samba").  Ubuntu doesn't install it by default.

---

