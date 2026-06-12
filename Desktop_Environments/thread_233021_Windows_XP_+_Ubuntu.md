---
title: "Windows XP + Ubuntu"
date: 2006-08-09
forum: Desktop Environments
---

### Post by Sethro on 2006-08-09
Iam a huge fan of ubuntu so far, its truly an amazing piece of software. I need your opinion I want to use VMWare and install Windows XP. The only sole purpose is that I want to be able to use Microsoft Office 2007 Beta 2. 

See here for a screenshot : [http://aarakast.de/wp-content/uploads/microsoft-office-2007.jpg](http://aarakast.de/wp-content/uploads/microsoft-office-2007.jpg)

Would it be possible for me to print any documents under Vmware?
Also would my wireless work in Vmware itself? 
Is using Vmware slow and painfull?

If I were to install iTunes would I be able to use my iPod normally?

---

### Post by reacocard on 2006-08-09
> Would it be possible for me to print any documents under Vmware?
if you use a usb printer
> Also would my wireless work in Vmware itself? 
vmware just uses your ubuntu network connection. if you have networking in ubuntu, you'll have networking in vmware. (you'll have to use ubuntu to configure the networking though.
> Is using Vmware slow and painfull?
this depends on your computer. you need lots of ram (at least 512MB), and a decent (2.4ghz+) processor for it to run well
> If I were to install iTunes would I be able to use my iPod 
probably, using USB.

---

### Post by Sethro on 2006-08-09
Very cool, now would I have to use Wine to install Vmware or is their an official linux version out there?

---

### Post by tzulberti on 2006-08-09
There is no need for installing wine when installing vmware. There is a vmware-player in the repos. But I think that maybe you should trie to install vmware-server (search the how-to section for this) because you need the image file of the Windows.

---

### Post by reacocard on 2006-08-09
there is the player in the repos. unfortunatly, it can't create virtual machines. you'l need vmware server (or a third-party service like easyvmx.com) to create the machine. you can get the linux version of vmware server from their site. just download the tarball and run the install script. there's also a few dependencies: xinetd, and the kernel headers for your running kernel.

---

