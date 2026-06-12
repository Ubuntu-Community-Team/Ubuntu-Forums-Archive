---
title: "wireless for d600?"
date: 2008-05-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aggiemarine07 on 2008-05-25
I have been searching for a long time to find a tutorial that explains how to get the wireless working on a Dell d600 in Hardy. Many people has written on here that their wireless for their d600 has worked out of box but mine is not. If someone could point me in the right direction towards a good tutorial I would greatly appreciate it. Thanks!

here is my output for lshw - C network

WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:a3:9a:69
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5702-v2.25 ip=192.168.2.5 latency=64 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:34:14:1d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by sam_delta on 2008-05-25
if you have a wired connection, plug it in update your system ,and check under system>administration>hardware drivers, if theres a broadcom wireless driver listed, just click on it and enable it

remember that you must have an internet connection and update your system to effectively check if there are drivers

if it doesn't appear, you'll have to install the drivers with a different procedure, but its worth checking if its listed under hardware drivers before trying anything as it might save time


sam

---

### Post by aggiemarine07 on 2008-05-26
done that Ive even re installed b43-fwcutter and nothing appears under the hardware drivers. I even did a fresh install with a internet connection attached during the install and nothing happens. After re-installing b43-fwcutter, it did however show that it as a wireless device but I still can not see any wireless networks.

---

### Post by sam_delta on 2008-05-26
how did you installed b43-fwcutter? using synaptic or apt-get?

sam

---

### Post by aggiemarine07 on 2008-05-26
apt-get

---

### Post by aggiemarine07 on 2008-05-26
I was browsing around the ubuntu tutorials for older versions and I came across some commands with ndiswrapper. Here is the output from those commands:

greg@greg-laptopwork:~$ sudo ifdown wlan0
ifdown: interface wlan0 not configured
greg@greg-laptopwork:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
greg@greg-laptopwork:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

Does this mean anything? Thanks.

---

### Post by sam_delta on 2008-05-26
do you have ndiswrapper installed? whats the output of 
```
ndiswrapper -l
```

sam

---

### Post by aggiemarine07 on 2008-05-27
Got it working, in the BIOS is had listed turn wireless on "fn+f2/Application". I changed it to just fn+f2 and now I can turn it on and off. Also, when it was set to fn+f2/application setting it was listed as "wireless off." Stupid me forgot to check the BIOS. Thanks for your help though!

---

### Post by sam_delta on 2008-05-28
glad its working,
enjoy ubuntu :)
sam

---

### Post by fiaf1 on 2008-05-28
> **aggiemarine07 said:**
> Got it working, in the BIOS is had listed turn wireless on "fn+f2/Application". I changed it to just fn+f2 and now I can turn it on and off. Also, when it was set to fn+f2/application setting it was listed as "wireless off." Stupid me forgot to check the BIOS. Thanks for your help though!


Hello and thanks in advance,

I have a D600 with 8.04 and I am trying to get my wireless working. I seem to have one fewer BIOS options than you. My BIOS options are: Off, Application, and fn+f2/application. fn+f2 option is not available. Am I missing something?

Did you have to do anything after you correct the BIOS?

Regards.

---

### Post by supremedalek on 2008-05-31
> **fiaf1 said:**
> Hello and thanks in advance,

I have a D600 with 8.04 and I am trying to get my wireless working. I seem to have one fewer BIOS options than you. My BIOS options are: Off, Application, and fn+f2/application. fn+f2 option is not available. Am I missing something?

Did you have to do anything after you correct the BIOS?

Regards.

I would leave it in the "fn+f2/application" mode. This way either you can turn it on using the function keys or an application can do the trick.

---

### Post by mayliffe on 2008-07-27
I have just installed Hardy Heron on two D600s (Among other things). The wireless works fine on the first one. On the second one, if I remember correctly, I had to install the Broadcom driver "manually" with aptitude. Wireless works fine if the first user to log in is the one I created when I set the system up. If the first log in user is someone else, even with all the admin user privileges set, then the wireless i/f does not work.

 lshw -C network
PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: ..:..:..:..:..:..
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5705-v3.16 latency=32 link=no mingnt=64 module=tg3 multicast=yes port=twisted pair
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: ..:..:..:..:..:..
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.x.xxx multicast=yes wireless=IEEE 802.11g

---

