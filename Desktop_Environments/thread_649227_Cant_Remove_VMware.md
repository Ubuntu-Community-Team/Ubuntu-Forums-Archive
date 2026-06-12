---
title: "Cant Remove VMware"
date: 2007-12-24
forum: Desktop Environments
---

### Post by silv3rback on 2007-12-24
Hi guys

I know this has been posted here a lot, but I've spent the past two day trying to find ways to remove my VMware install.... still no luck

I've tried sudo apt-get remove vmware
I've tried ./vmware-uninstall.pl
And looked around a few other threads about it, something with purge, and aptitude etc
You have to excuse me, Im a big time no0b with Linux


Any other ideas on how to remove it?

---

### Post by adam.tropics on 2007-12-24
which method did you use to install it?

---

### Post by silv3rback on 2007-12-27
I unpacked it, and run vmware-install.pl

---

### Post by adam.tropics on 2007-12-27
If you unpacked it, presumably to your home directory, in terminal cd to /home/<username>/vmware-player-distrib/bin then run the uninstall script from there, with sudo. The folder would be named differently for server but as far as I know, the idea would be the same. (I know you said you'd tried the script,just, from where, and as what user?)

---

### Post by Kenbeinside on 2007-12-27
> **silv3rback said:**
> Hi guys

I know this has been posted here a lot, but I've spent the past two day trying to find ways to remove my VMware install.... still no luck

I've tried sudo apt-get remove vmware
I've tried ./vmware-uninstall.pl
And looked around a few other threads about it, something with purge, and aptitude etc
You have to excuse me, Im a big time no0b with Linux


Any other ideas on how to remove it?

did u  try synaptic?

---

### Post by emmerc on 2008-01-01
I installed vmware using synaptics and then I removed it using synptics so no problem in that respect but my hard drive still is missing 4GB I used to create the virtual machine. I have tried even erasing manually the .vmx files and still the storage space is missing. I am using a 15GB HD so space is an issue for me in this case. Does someone can help me to free that space? I do appreciate your help!

Emmer Chacon

---

### Post by daulex on 2008-01-05
got the same problem, cant find the solution :( plz help

---

