---
title: "Edubuntu 10.04 VMware VM ready for download"
date: 2010-06-04
forum: Education &amp; Science
---

### Post by lichenghsu on 2010-06-04
Basically, this is a VMware virtual machine I build for a teacher of elementary school and a teacher of high school. But I think it maybe useful for others as well, so I release it for public download.

Following is the information of this virtual machine:

Edubuntu 10.04
==============

This is an Edubuntu 10.04 VMware virtual machine.

File Name: edubuntu-10.04-desktop-i386-vmware-20100602.7z
File Size: 884 MB
MD5 Checksum: 33fa2b384f81c2ed30682cfb9d3e3744

Download Method
===============

Download virtual machine directly from depositfiles.com.

[http://depositfiles.com/files/mt74gzknc](http://depositfiles.com/files/mt74gzknc)

To unpack the virtual machine, you need 7-Zip file archiver.

Please visit

[http://www.7-zip.org/](http://www.7-zip.org/)

for more information.

Description
===========
This is a VMware virtual machine from Happy Penguin, Taiwan
([http://happypenguin.tw/](http://happypenguin.tw/)) for evaluating Edubuntu 10.04.

Edubuntu ([http://www.edubuntu.org/](http://www.edubuntu.org/)) is a Linux-based operating
system that provides the latest educational applications in free
and open source software.

System Requirements
===================
* Standard x86-compatible or x86-64-compatible PC
* Processor speed – 2.0 GHz or faster
* Memory – 1 GB minimum (2 GB recommended).
You must have enough memory to run the host operating system,
the virtual machine, and applications on the host and guest
operating systems.
* Linux, Windows or Mac OS X as host operating systems

Compatible Products
===================
VMware Player 2.5 or later
VMware ACE 2.5 or later
VMware ESX Server 4.0 or later
VMware Fusion 2.0 or later
VMware Server 2.0 or later
VMware Workstation 6.5 or later

HOWTO
=====
Just download the virtual machine archive, unpack it, open with
the free VMware player ([http://www.vmware.com/products/player/](http://www.vmware.com/products/player/))
and start running!

Virtual Machine Details
=================
Processors: 2 CPUs (can add more later)
Memory: 768 MB (can be modified later)
Hardisk: 16.0 GB, dynamic (can add additional hardisks)
Ethernet: NAT (can be changed later)
Resolution: 800x600 (can be changed later)
VMware Tools: Installed

Recompile official Ubuntu Linux kernel for optimization,
makes it more compact and virtual machine friendly.

It should now run faster and need less resources than
the one comes with Ubuntu distribution.

Network settings
================
IP, DNS, default gateway: auto configuring on boot by DHCP

Login Account
=============
Username: penguin
Password: happypenguin.tw


That's it.

Have fun  :)

---

### Post by lichenghsu on 2010-06-09
No more BitTorrent, and no more Deposit Files, you can download the virtual machine directly from sourceforge.net now. :)

[edubuntu-10.04-desktop-i386-vmware-20100602.7z]("http://sourceforge.net/projects/happypenguin/files/edubuntu/edubuntu-10.04-desktop-i386-vmware-20100602.7z/download")

---

### Post by peter444 on 2010-06-28
Thank you for a nice version of Edubuntu , currently running it on a XP host, had to change virtual machine settings to one CPU

One problem with VM Ware 3.1 download was the installer hanging at the splash screen, found the answer to the problem here

[http://communities.vmware.com/message/1480236](http://communities.vmware.com/message/1480236)

"**When I downloaded VMware Player installer to my download directory and ran it from there, the VMware Player installer grabs that file and displays it since it's in the same directory. So all I had to do was delete the INDEX.HTM file, and I was able to install the VMware Player. Apparently that's the behavior of the installer- if it has an INDEX.HTM in the installer, that it will use like-named files from the current directory?"** 

So I just created a new directory for the VM Player download and then the installer worked ok

Regards, Health, Wealth and Happiness for the future

---

### Post by lichenghsu on 2010-07-01
Thanks, peter444 :)

I have no machine running Windows for a while, so I can't check the situation. But, yes, this is very important information for any user running Windows as host OS.

Thanks for sharing. :)

---

