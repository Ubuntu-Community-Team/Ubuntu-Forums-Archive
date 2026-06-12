---
title: "Network Card not detecting"
date: 2010-10-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by krishnik on 2010-10-17
Hi,
I have a dell inspiron n4010 laptop. i have installed both windows7 and ubuntu 10.04. I have a bsnl broadband connection which is working perfectly in windows but when i use ubuntu its not connecting to the internet. The ethernet light on the modem is not blinking when i use ubuntu. But its working in windows.

I tried sudo dhclient eth0 but it showed an error like "no network interface detected" [Not the exact error msg]

Please help me

---

### Post by dineshs on 2010-10-17
Can you post the result of```
sudo lshw -C network
```when modem is connected

---

### Post by krishnik on 2010-10-22
> **dineshs said:**
> Can you post the result of```
sudo lshw -C 
network
```when modem is connected

Thank you dineshs for the reply
Here is the result
```
*-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)
```

---

### Post by dineshs on 2010-10-22
A similar thread but solved
[http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697)

---

### Post by krishnik on 2010-10-23
> **dineshs said:**
> A similar thread but solved
[http://ubuntuforums.org/showthread.php?t=1505697](http://ubuntuforums.org/showthread.php?t=1505697)


WOW it worked............ Thanks a lot .... here is the solution that worked for me

1. Download official Atheros driver, from their website: [http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)  (file: AR81Family-linux-v1.0.1.9.tar.gz)
2. tar -xvf AR*
3. make
4. sudo make install
5. restart


Thank you dineshs..............

---

### Post by dineshs on 2010-10-23
Thanks to pytheas22 :)

---

