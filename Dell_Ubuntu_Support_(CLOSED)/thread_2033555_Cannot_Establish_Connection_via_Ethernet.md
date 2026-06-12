---
title: "Cannot Establish Connection via Ethernet"
date: 2012-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Newbsylberry on 2012-07-26
Hi all, 

I am new to ubuntu. Total beginner. I am running Ubuntu 10.04 and am not able to establish a network connection via ethernet port. I have tried edit network connections and typed in all my network information but nothing happens. I have also done the sudo lshw -C network command and it tells me my network is UNCLAIMED but recognizes my ethernet cable (below). I have also come across a possible solution that involves building kernel modules but this is much too complicated for my level of expertise. I was wondering if any of you had a solution to this problem?


freesurfer3@freesurfer3-desktop:~$ sudo lshw -C network
[sudo] password for freesurfer3:
*-network UNCLAIMED
description: Ethernet controller
product: Intel Corporation
vendor: Intel Corporation
physical id: 19
bus info: pci@0000:00:19.0
version: 04
width: 32 bits
clock: 33MHz
capabilities: pm msi bus_master cap_list
configuration: latency=0
resources: memory:e1600000-e161ffff memory:e1680000-e1680fff ioport:4040(size=32)
freesurfer3@freesurfer3-desktop:~$

---

### Post by 2F4U on 2012-07-26
Where do you usually get your IP address from, for example, a router?

---

### Post by Newbsylberry on 2012-07-26
Sorry I don't know if this will be much help but the computer is at a university so we obtain our IP from an ethernet wall port. However our machine is dual-boot and the internet works fine on the windows side.

---

### Post by Cheesehead on 2012-07-26
Try the command [FONT="Courier New"]dmesg | grep eth[/FONT] and paste the entire result here.

When you typed in all your network information, where did you do that? In Network Manger? Someplace else? Exactly what information did you provide?

---

### Post by Newbsylberry on 2012-07-30
We typed it in under the airport-like thing at edit networks.

---

