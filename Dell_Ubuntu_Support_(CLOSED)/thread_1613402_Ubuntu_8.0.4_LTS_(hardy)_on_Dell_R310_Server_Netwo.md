---
title: "Ubuntu 8.0.4 LTS (hardy) on Dell R310 Server: Network Card  Issues"
date: 2010-11-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chyanga on 2010-11-04
I have Dell R310 sever. I  tried to install Ubuntu 8.0.4 LTS (hardy) using the CD ROM. 

I couldn't  install using the cdrom. It gave driver not found message at the middle of the install and aborted (but CDROM hardware works fine with live CD). 



Then, I used the usb boot drive and installed the Ubuntu from there. I came up with some issues: 



  
2.       After, I installed the image , couldn’t bring the network interfaces up.I checked the /etc/inetwork/interfaces files. It looks good as :


# The loopback interface
auto lo
iface lo inet loopback

# The static network for internal network

auto eth0

iface eth0 inet static
   address 10.120.16.22
   netmask 255.255.255.0
   gateway 10.120.16.21



I tried couple of commands :

ifconfig -a --> only shows loopback

I tried --> /etc/init.d/networking restart

gave this errors: 

eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device: ls 



 Sudo ifup eth0
Sudo ifup eth1
It didn’t bring the interfaces up;
Gave some errors :    
  eth1: ERROR while getting interface flags: No such device 
  SIOCSIFADDR: No such device
   
   
  I also run the command, 
                  
   lshw –C network 



gave :

   
  *-network:0 UNCLAIMED
                  Description: Ethernet controller
                  Product: NetXtreme II BCM5716 Gigabit Ethernet 
                  Vendor:Broadcom Corporation
                  Physical id:0
                  Bus info: [EMAIL="pci@0000:02:00.0"]pci@0000:02:00.0[/EMAIL]
                  Version:30
                  Width :64 bits
                  Clock: 33MHz
                  Capabilities: pm vpd msi msix pciexpress bus_master cap_list
                  Configuration: latency =0
   
  Same for the another network card. 
   
  Note: I read somewhere that Dell R310 comes with newest Broadcom Ethernet card, but the Ubuntu 8.0.4 LTS (hardy), comes with older version of the driver, so the OS doesn’t detect the Network card. I am struggling little bit to figure out this, spend some time , but couldn’t figure how to update the drivers. 



Any help would be greatly appreciated. 





Regards, 

Chyangba

---

### Post by truant on 2011-01-05
The latest LTS has the network drivers for the Broadcom NXII cards on it.

Unless you have a very good reason for using such an old version of Ubuntu, I'd suggest using 10.04 instead of 8.04

---

