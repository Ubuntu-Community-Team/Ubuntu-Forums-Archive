---
title: "Unable to browse windows share"
date: 2009-02-26
forum: Desktop Environments
---

### Post by svavark on 2009-02-26
I have installed ubuntu 8.10 desktop, ran all the updates and everything looks good.
But I have a windows2003 domain also and when I browse the network I see 
Windows networks, 
See the domain, 
see the servers in the domain
 but when I click on the server - and expect to see the shares on that machine - nothing gets listed?
My son has a Macbook with OsX with same problem.
"Neddless" to say my XP has no problem :=):lolflag:
Any ideas?

TIA  Svavar

---

### Post by smani on 2009-02-26
Maybe you are experiencing a bug in gvfs that prevented shares of some OS's from being listed - a fix was released (at least in the proposed updates for intrepid) a few weeks ago - try updating your system (you can enable proposed updates in system -> administration -> software sources). Alternatively, if you specify the exact path, you should be able to access the share, i.e. write in the nautilus address field
smb://myserver/myshare

---

