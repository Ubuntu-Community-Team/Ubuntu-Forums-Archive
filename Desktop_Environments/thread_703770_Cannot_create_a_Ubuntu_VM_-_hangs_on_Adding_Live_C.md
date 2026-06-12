---
title: "Cannot create a Ubuntu VM - hangs on Adding Live CD User"
date: 2008-02-21
forum: Desktop Environments
---

### Post by bhuber on 2008-02-21
Yes, I've read a bunch of forums and threads on this topic and could never find a solution...That said, here's my situation - 

I'm trying to create a new VM running Ubuntu 6.061-386 LTS. 
I'm running VMWare Workstation version 6.02 build 59824, with a base OS of Ubuntu 6.061.  
In the VM wizard I select Linux/Ubuntu. The cd boots successfully and starts the Ubuntu installer. It goes through the first few steps, then hangs on "Adding Live CD User". I have validated the md5sum of the Ubuntu disk to be correct, and have actually loaded it onto another system as the base OS without problem. It only hangs when trying to create a guest OS in a VM. 
I also tried the alternate Ubuntu installer and it complained about errors reading the disc. Any ideas? Since I can build a base OS with the disk, I'm thinking it is a VMware issue.

Thanks,
Bob

---

### Post by bhuber on 2008-02-21
I figured this out...at least for me. I copied my ISO image to the hard disk.  Then I created a new VM, powered it on, and then went to the VM menu and selected Removeable devices, then CDROM, then Edit.  I selected Use ISO Image and pointed it to the copy of the ISO on the hard drive.  Saved it, powered back up and it worked.

---

