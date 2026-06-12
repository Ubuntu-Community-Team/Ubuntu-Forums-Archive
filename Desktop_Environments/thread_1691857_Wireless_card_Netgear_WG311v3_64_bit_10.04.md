---
title: "Wireless card Netgear WG311v3 64 bit 10.04"
date: 2011-02-20
forum: Desktop Environments
---

### Post by CJ_Hudson on 2011-02-20
I have tried to get this card working, and have googled it with some success in the archives ( [http://ubuntuforums.org/showthread.php?t=320111](http://ubuntuforums.org/showthread.php?t=320111), where I downloaded the WG311v3 64 bit AMD driver), read the installation guides and Wikis etc. but to no avail.

The card is showing as present in -> Admin ->  Windows Wireless Drivers, however, when I  iwconfig in the terminal I get:

lo        no wireless extensions.

eth0      no wireless extensions.

ifconfig gives the wired connection and:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

I have been through the full process of blacklisting the existing wireless drivers, making sure ndiswrapper is installed,identifying my wireless adapter:

01:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

,getting the pc id:

11ab:ifaa

, so cannot understand why it isn't working.
I am running Lucid Lynx 10.04 64-bit with an Asus P5L-VM1394 motherboard and Dual-Core E2200 processor.

However I do get one strange error message, perhaps someone could enlighten me, when I type ndiswrapper -l in the terminal I get:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg311v3 : driver installed
	device (11AB:1FAA) present

Finally when I type

tail /var/log/messages

I get:

Feb 20 18:22:14 chris-desktop kernel: [   19.952880] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
Feb 20 18:22:14 chris-desktop kernel: [   19.952889] ndiswrapper (mp_halt:262): device ffff8800b2f08680 is not initialized - not halting
Feb 20 18:22:14 chris-desktop kernel: [   19.952893] ndiswrapper: device eth%d removed
Feb 20 18:22:14 chris-desktop kernel: [   19.952907] ndiswrapper 0000:01:0a.0: PCI INT A disabled
Feb 20 18:22:14 chris-desktop kernel: [   19.952923] ndiswrapper: probe of 0000:01:0a.0 failed with error -22
Feb 20 18:22:14 chris-desktop kernel: [   19.953003] usbcore: registered new interface driver ndiswrapper
Feb 20 18:22:15 chris-desktop kernel: [   21.245315] [drm] nouveau 0000:04:00.0: Allocating FIFO number 2
Feb 20 18:22:15 chris-desktop kernel: [   21.250125] [drm] nouveau 0000:04:00.0: nouveau_channel_alloc: initialised FIFO 2
Feb 20 19:02:06 chris-desktop kernel: [ 2412.143116] UDF-fs: Partition marked readonly; forcing readonly mount
Feb 20 19:02:06 chris-desktop kernel: [ 2412.183390] UDF-fs INFO UDF: Mounting volume 'Asus_p5l_VM_1394_Drivers', timestamp 2008/08/02 13:15 (1000)

I have edited etc/modules to start ndiswrapper on system startup, and loaded the .inf file successfully with the admin tool.

The only thing I can think of is that the 64 bit driver is AMD and I don't have an AMD processor, I have an Intel one, in which case I require the 64 bit Intel driver.

Sorry quick edit here. Does this output from sudo lshw

 *-network UNCLAIMED
                description: Ethernet controller
                product: 88w8335 [Libertas] 802.11b/g Wireless
                vendor: Marvell Technology Group Ltd.
                physical id: a
                bus info: pci@0000:01:0a.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=64
                resources: memory:cbef0000-cbefffff memory:cbee0000-cbeeffff

..mean that it can never work with a 64 bit system? i.e. Width is 32 bits?

---

### Post by CJ_Hudson on 2011-02-21
Bump.

---

### Post by grahammechanical on 2011-02-21
Please, do not get your bits in a twist.

I am running a 64bit Intel core2 Duo CPU and I am running on it the 64bit version of Ubuntu despite the fact it is has the letters AMD somewhere in the name. There does not exist a 64bit Intel version of Ubuntu. You only need to make sure that you are running the 64bit Ubuntu on a 64bit CPU from either AMD or Intel and not trying to run it on a 32bit CPU. The 32bit Ubuntu will work fine on either a 32bit CPU or a 64bit CPU. It sounds illogical but 64bit CPUs are designed to run 32bit OS.

When I run the command lshw I see that I have many devices on the motherboard that have a width of 32bits, including the USB devices and the ethernet device. Just like you. It is not a problem. The motherboard is design so that all these devices work together.

Concentrate on getting wireless to work. As you are using a 64bit OS  then the driver for the wireless card would also need to be classed as  64bit. If you were using a 32bit OS then you would need a driver classed  as working on a 32bit OS.

Regards.

---

### Post by thefasterblueone on 2011-02-21
This card should work no problem. check this link.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB") 

Please post the output of:

```
sudo lshw -C network
```

---

### Post by CJ_Hudson on 2011-02-22
> **thefasterblueone said:**
> This card should work no problem. check this link.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB") 

Please post the output of:

```
sudo lshw -C network
```

Hi thefasterblueone,
Here is the output:

 *-network               
       description: Ethernet interface
       product: L1 Gigabit Ethernet Adapter
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:18:f3:21:3f:fd
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1 driverversion=2.1.3 duplex=full firmware=N/A ip=192.168.0.13 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:cbfc0000-cbffffff memory:cbfa0000-cbfbffff(prefetchable)
  *-network
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=ndiswrapper latency=64
       resources: irq:22 memory:cbef0000-cbefffff memory:cbee0000-cbeeffff
chris@chris-desktop:~$ 
 
  Thanks.

B.T.W. I cannot find anything about the blacklisted modules in this link in the link you gave:

"
WG311v3
	

Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
	
...

(Hardy) Worked after installing ndiswrapper and a Windows driver. WPA not supported. Follow instructions at 

[www.help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](www.help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3) 
"

These are the ones pre-installed in Ubuntu, but since the version of Ubuntu has changed they also may have changed since I got these instructions:

"
Edit the /etc/modprobe.d/blacklist  file and add:
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
"
?

P.S. I checked the link initially, it's where I got the 64 bit AMD driver. Thankyou! (-:
P.P.S. Thanks grahammechanical, that is reassuring.

Sorry this looks so messy, I haven't learned how to use the 'Code' box yet!

---

### Post by CJ_Hudson on 2011-02-24
Bump.

---

### Post by CJ_Hudson on 2011-02-25
Bump.

---

### Post by thefasterblueone on 2011-02-25
I made a mistake when I said your card should work, I was looking at WG111v3.

Maybe this link can help, but you probably already tried it.

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")

---

### Post by CJ_Hudson on 2011-02-26
> **thefasterblueone said:**
> I made a mistake when I said your card should work, I was looking at WG111v3.

Maybe this link can help, but you probably already tried it.

[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")

Yes, thankyou, I have tried everything in this link.

One thing I am not sure about, is if I try force-installing the 32 bit driver (force installing 32 bit software into 64 bit as described in this link: [http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)) in case the 64 bit one doesn't work (on my system)?

I am completely new to 64 bit Ubuntu, I got the 32 bit driver to work with 32 bit Ubuntu, but  the problem is the 64 bit forum is now closed.

Any additional help and any further suggestion gratefully recieved.

---

### Post by CJ_Hudson on 2011-02-27
Bump.

---

### Post by CJ_Hudson on 2011-02-28
Bump.

---

