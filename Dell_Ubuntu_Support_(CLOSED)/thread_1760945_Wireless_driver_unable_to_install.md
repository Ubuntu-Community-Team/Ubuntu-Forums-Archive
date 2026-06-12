---
title: "Wireless driver unable to install"
date: 2011-05-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Aarontex40k on 2011-05-17
I have a Dell Studio XPS 13''
I have not modified the hard where at all.
I have bin trying to install the wireless driver (Broadcom STA wireless driver) ever sense I just put Ubuntu 11.04 on it. 

This is what the "Additional Drivers window tells me about the driver:

This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.

When I try to install it the response is:

Sorry, installation of this driver failed.
Please have a look at the log file for details: /var/log/jockey.log

This is the /var/log/jockey.log:

(((Attached)))

Can anyone help me with this?

---

### Post by westie457 on 2011-05-17
Hello, you are not the first to have this problem and probably will not be the last. 

The solution goes as follows:-  

f you have an ethernet cable plug it in and do the following instructions in the order they are written.

1) In synaptic package manager search for bcm (not in the quick search box) and mark the ones with a green box for complete removal. Click apply.

2) Reboot

3) When you have rebooted go into synaptic again and do another search for bcm. Mark the package 'b43-fwcutter' and the 'firmware-b43-installer' package. Click apply.

4) Reboot.

You should now have a working wireless connection.

If not then go to this page

[http://ubuntuforums.org/showthread.php?t=1604868&page=24](http://ubuntuforums.org/showthread.php?t=1604868&page=24)

Read and follow the instructions in post #240 written by 'josephmills'

It is a comprehensive guide on what to do and what is needed.

---

### Post by Aarontex40k on 2011-05-17
@westie457 Thanks. Im going to try this when I get home from work.

---

### Post by westie457 on 2011-05-18
> **Aarontex40k said:**
> @westie457 Thanks. Im going to try this when I get home from work.

Have you tried this yet?

Suddenly remembered you should _not_ do the first reboot.

I did and completely killed all networking on my laptop.

Apologies if this warning is too late.

---

### Post by Aarontex40k on 2011-05-18
no i have not dun it yet. I hope it works out for me.

---

### Post by Aarontex40k on 2011-05-18
> **westie457 said:**
> Hello, you are not the first to have this problem and probably will not be the last. 

The solution goes as follows:-  

f you have an ethernet cable plug it in and do the following instructions in the order they are written.

1) In synaptic package manager search for bcm (not in the quick search box) and mark the ones with a green box for complete removal. Click apply.

2) Reboot

3) When you have rebooted go into synaptic again and do another search for bcm. Mark the package 'b43-fwcutter' and the 'firmware-b43-installer' package. Click apply.

4) Reboot.

You should now have a working wireless connection.

If not then go to this page

[http://ubuntuforums.org/showthread.php?t=1604868&page=24](http://ubuntuforums.org/showthread.php?t=1604868&page=24)

Read and follow the instructions in post #240 written by 'josephmills'

It is a comprehensive guide on what to do and what is needed.
I am unable to do step 1. It comes back with an error. I am able to install the things on step 4. I'm going to try a reboot and see what happens.

---

### Post by jessicansir on 2011-07-15
Did you ever get it to work? I am having the same problems.

---

### Post by Aarontex40k on 2011-07-15
I'm sorry for not conferming that I was able to get it to work. I do not remember how I got it to work because it was quite a long time ago. I think it was the way stated last buy the person helping me. I am having a new problem with the wifi but I think it is a hard where malfuncktion and unrelated. Thanks for your help.

---

### Post by nm_geo on 2011-07-15
> **jessicansir said:**
> Did you ever get it to work? I am having the same problems.

You may have the same problem, but not the same resolution.
Copy and paste the following in terminal.
```

lspci -nn | grep 0280
```

```
rfkill list all
```

```
sudo lshw -C network
```

Paste the results here and someone can help you.

---

### Post by jessicansir on 2011-07-16
ubuntu@ubuntu:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
ubuntu@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:60:e4:c9
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.143 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)
ubuntu@ubuntu:~$

---

### Post by nm_geo on 2011-07-16
> **jessicansir said:**
> ubuntu@ubuntu:~$ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
ubuntu@ubuntu:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:60:e4:c9
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.143 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)
ubuntu@ubuntu:~$

  Ok your wireless card needs b43-fwcutter and firmware-b43-lpphy-installer.

You can check in Synaptic by doing a search on _bcm_  remove any other modules you see that are green and install those two packages.

Then reboot without ethernet cable.  Let's see what happens. Read the properties on the firmware if you like.

---

### Post by jessicansir on 2011-07-17
Thanks for helping, I appreciate it. I ran the search, looking in Description & Name for "bcm". Two packages were green: bcmwl-kernel-source and libklibc. I marked both for complete removal and clicked apply, despite warnings about rendering system unusable. I got an error message in return. So I tried just removing bcmwl-kernel-source, but got an error saying "E: bcmwl-kernel-source: subprocess installed post-removal script returned error exit status 1" Despite the errors, it appears that I have affected something because now when I unmark the packages bcmwl-kernel-source is highlighted red and has a red X next to the name. Should I be worried?

Also, under Synaptic's Quick Search filter, I found that I can pull up b43-fwcutter, but I can't find firmware-b43-lpphy-installer anywhere.

---

### Post by nm_geo on 2011-07-18
> **jessicansir said:**
> Thanks for helping, I appreciate it. I ran the search, looking in Description & Name for "bcm". Two packages were green: bcmwl-kernel-source and libklibc. I marked both for complete removal and clicked apply, despite warnings about rendering system unusable. I got an error message in return. So I tried just removing bcmwl-kernel-source, but got an error saying "E: bcmwl-kernel-source: subprocess installed post-removal script returned error exit status 1" Despite the errors, it appears that I have affected something because now when I unmark the packages bcmwl-kernel-source is highlighted red and has a red X next to the name. Should I be worried?

Also, under Synaptic's Quick Search filter, I found that I can pull up b43-fwcutter, but I can't find firmware-b43-lpphy-installer anywhere.

It is not necessary to do complete removal.. reinstall the  libklibc in Synaptic..

Then In terminal with ethernet cable connected.

```
sudo apt-get update

``````
sudo apt-get upgrade
```

The update & upgrade may take a while.. Many packages on a new install.. 

```
sudo apt-get install firmware-b43-lpphy-installer
```If you could not re-install libklibc in Synaptic.

```
sudo apt-get install libklibc
```Remove ethernet cable reboot and click on network manager icon top right area sign up your wireless.

---

### Post by jessicansir on 2011-07-21
This is depressing: I am still unable to affect libklibc.    	 	 	 	 	 At the end of running the upgrade the Terminal read: “Removing bcmwl-kernel-source ... 
 update-initramfs: deferring update (trigger activated) 
 lzma: Encoder error: -2147467259 
 dpkg: error processing bcmwl-kernel-source (--remove): 
  subprocess installed post-removal script returned error exit status 1 
 Errors were encountered while processing: 
  bcmwl-kernel-source 
 E: Sub-process /usr/bin/dpkg returned an error code (1) ”


Subsequently, 

"ubuntu@ubuntu:~$ sudo apt-get install firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-lpphy-installer"


...and the sudo command for reinstalling libklibc returned the same error report as the one at the end of the upgrade. 



Maybe this is a product of running a pen drive Linux?

---

### Post by avnish123 on 2011-07-21
[COLOR=#000000][FONT=Times New Roman][LEFT][FONT=Arial]Based in Lisbon, Portugal, EliteKeys.com began in 2010 to provide our customers with a widely-available, quick and secure way to purchase game time codes and registration keys. Every day we help fight fraudulent purchases through our anti-fraud verifications and quick responsiveness to customer issues.[/FONT][/LEFT][/FONT][/COLOR]

---

### Post by nm_geo on 2011-07-21
> **jessicansir said:**
> This is depressing: I am still unable to affect libklibc.                             At the end of running the upgrade the Terminal read: “Removing bcmwl-kernel-source ... 
 update-initramfs: deferring update (trigger activated) 
 lzma: Encoder error: -2147467259 
 dpkg: error processing bcmwl-kernel-source (--remove): 
  subprocess installed post-removal script returned error exit status 1 
 Errors were encountered while processing: 
  bcmwl-kernel-source 
 E: Sub-process /usr/bin/dpkg returned an error code (1) ”


Subsequently, 

"ubuntu@ubuntu:~$ sudo apt-get install firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-lpphy-installer"


...and the sudo command for reinstalling libklibc returned the same error report as the one at the end of the upgrade. 



Maybe this is a product of running a pen drive Linux?

I was assuming that you had an installed Ubuntu version.  Yes, sometimes it is difficult to get the wireless working if you are running off the Live CD or USB, and even if you are able to get it working it might not be able to work after a reboot

---

### Post by jessicansir on 2011-07-21
:( Bummer, but thanks so much for your help anyways!

---

