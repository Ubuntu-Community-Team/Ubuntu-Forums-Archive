---
title: "Home Server - To VM or Not"
date: 2009-04-21
forum: General Help
---

### Post by BLo on 2009-04-21
Hi All,
I know there is already a ton of Home server threads out there but I couldn't the answer I was looking for

I've decided to build myself a home ubuntu server for a fileserver & keeping my torrents in check but also to learn a bit.

I ideally would like to eventually build a server that can:
•	share files between both windows and linux computers (Samba)
•	Remote administration of Torrents (via torrentflux)
•	backup of documents on other computers (rsync) 
•	Access computer from anywhere
•	(Any other Suggestions?)

I've found some guides to do these. (but any other guides are welcome)

But eventually I'd like to also turn the box into a router / firewall as well, being able to shape traffic to the PCs on the network. Maybe more if I get any ideas.

Someone has suggested that I create different VMs for each 'service' that way any issues I run into should only affect that VM.

I still haven't bought my hardware yet and my question would be: 
1.	Is VMs the way to go? Is the overhead of running each 'service' on a VM worth it?
2.	What kind of hardware specs will I need to do this, for using VMs and not?  Ideally I don’t want to spend a huge amount

---

### Post by buck2825 on 2009-04-24
IMO, ubuntu is solid if you want all that stuff on one brand of OS, (all ubuntu) then I would say forget the VM

I have a file server at the house and it is running vmware server with a win XP,  this is my only windows install.  it is there for when I must use windows.  

VM ware also makes a product called ESXi it is a very low level "OS"  that the only thing it does is run VMs.  so instead of a blotted OS running a Blotted os to do all the work it is a slimmed down barebones os running a full blotted os to do the work.

---

