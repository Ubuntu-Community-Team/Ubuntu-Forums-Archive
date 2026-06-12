---
title: "Need help with Averatec 3715-EH1 issues (dapper!)"
date: 2009-02-12
forum: General Help
---

### Post by acalafra on 2009-02-12
Hello, I have been trying to get my friends laptop in order for a few days. It has a few issues. For one the battery doesn't work at all so it needs the cord but thats not the problem. It had a messed up windows installation so I brought it to work and we used a usb CD rom to boot up windows but it failed during the install after overheating. So now I dont have the usb cd-rom and I have to use the internal optical drive, but now I have a big fan. The windows disk wont boot up, I tried ubuntu and linux mint, linux mint got almost to a full desk top and then failed. most other boot disks fail early on.

The only thing I could get to install on this laptop so far is the ubuntu 6.06.1 alternate i386 text installer

This installation brings me to a command line login. I can login.
I can do a "startx" and it brings me to a pretty snappy normal seeming ubuntu desktop. except most of the administration menu fails with a "gksu" command or file not found error. also there is no option for shutdown or restart. 

cat /proc/cpuinfo shows that the processor is running at 802Mhz which is good because it is no longer overheating. I had to use a huge fan to cool it off during the installation where I believe it runs at the bios speed of 1.8Ghz. 

I checked inittab and its default runlevel is 2. Why is it still going to a commandline.

I was going to try to upgrade with a CD because I can't get networking up yet. how do I do that

I cant cut and paste code blocks so please use "| grep" for your requests for info. lol I've read a lot of this forum, not so many posts. But I really need help with this, and probably a few other things that will go wrong with this laptop. 

I have been all over googling so I'll put links to what I've found so far

specs:
    * Notebook Computer
    * Hard Drive Interface: ATA 133, 80GB Hard Drive Capacity
    * 512MB; DDR Memory
    * 56KB Modem; Mobile AMD Sempron Processor ; 800 MHz System Bus
    * 12.1" Screen , 1024x768 Resolution ; XGA Display
    * 802.11b/g Wireless Capabilities
    * 8x; 24x
    * 3 USB Ports, Memory Card Slot Ports
    * Software Included: Microsoft Windows XP Home Edition
    * Also Features 1 Year Warranty
    * 10/100 Ethernet LAN Network Card ; VIA/S3 UniChrome Pro Graphics
    * Battery Lasts Up to 3.5 hrs.
    * 10.7"Wx8.7"Dx1.15"H "; 4.2 Lb.


Linux-on-laptops page:
[http://opalescent.ca/averatec_3700-ed1.html]("http://opalescent.ca/averatec_3700-ed1.html")


For Taking apart averatec 3700 series laptops:
[http://www.larwe.com/technical/av3715-open.html]("http://www.larwe.com/technical/av3715-open.html")

---

