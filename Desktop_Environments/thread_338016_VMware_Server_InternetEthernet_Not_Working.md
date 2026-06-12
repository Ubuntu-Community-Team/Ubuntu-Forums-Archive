---
title: "VMware Server Internet/Ethernet Not Working"
date: 2007-01-13
forum: Desktop Environments
---

### Post by cybrkup on 2007-01-13
Hi all, 

Kubuntu newbie here. I recently installed VMware server following the guide in the Support Section of this site. I am using it to run WinXP Home. Everything seems to be working fine except that I cannot connect to the internet with it. The Ethernet connection has a red X in the VM application so of course it does not work in XP.

Error message that I get:
Could not open /dev/vmnet0: No such file or directory
Failed to connect virtual device Ethernet0.

I did install all the other required applications prior to installing VMware and I also subsequently installed the VM Tools. I used all the default settings for the installation. I have tried Bridged, NAT and all the other choices without success. ](*,)  The internet works fine for Kubuntu 6.10. I have a cable modem with Earthlink. 

I'm not sure what other info will be needed, but any help will be appreciated. Thanks in advance.

CybrKup

---

### Post by cybrkup on 2007-01-14
A few settings in case they help....
interface is eth0
ip address is 192.168.0.2
default gateway ip is 192.168.0.1
protocol dhcp

---

### Post by MrGando on 2007-09-24
Hi there, I had a similar problem... you could try the following...

Go into terminal and then do:

cd to the directory that the virtual_machine_name.vmx is located

then do

sudo gedit Virtual_Machine_Name.vmx


Then with gedit, find the line that says 

# First network interface card

replace that whole part with 

# First network interface card
ethernet0.present= "true"
ethernet0.startConnected = "true"
ethernet0.virtualDev = "vlance"
ethernet0.connectionType = "bridged"



Good luck!

---

