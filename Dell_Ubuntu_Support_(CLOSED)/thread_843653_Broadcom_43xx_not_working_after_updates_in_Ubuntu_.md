---
title: "Broadcom 43xx not working after updates in Ubuntu 8.04 (Dell Inspiron 1720)"
date: 2008-06-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by obloxeon on 2008-06-28
I'm running Ubuntu 8.04 and after using the software update, my wireless no longer works. It doesn't connect on startup, it doesn't even show up.

sudo lshw -class network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

I can get it to work if I go to the restricted drivers manager, uninstall it and then re-enable it, assuming I have a wired connection, but after restart, nothing. I have to do the process over and over again. I wish I never updated through the software updates... how can I get this back to working?

---

### Post by obloxeon on 2008-06-29
Fixed.

---

### Post by A_Fiachra on 2009-09-20
> **obloxeon said:**
> Fixed.

How did you fix it??

---

### Post by A_Fiachra on 2009-09-21
I am in a very similar situation: Dell Inspiron 1545 with Broadcom wireless and I simply can not get the wireless working.

```

root# lshw -class network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:f9:80:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl3 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg


```

But .... iwlist tells me:

```

# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument


```


Zoinks!!!!!!!!!!


I've been fiddling with this for a few days, no luck


This card was working at one point -- out of the box.  I started installing modules, got into a corrupt state and backed off to the factory ISO.  Since then it's been iffy -- I had it working for a few days -- when I rebooted the system it went away (so, I never really had the wireless network set up correctly).

If I try to bring the interface up manually I get this interesting error:

```

# dhclient eth1
...

No DHCPOFFERS received.
No working leases in persistent database - sleeping.
resolvconf: Error: /etc/resolv.conf must be a symlink
 * Reloading /etc/samba/smb.conf smbd only
   ...done.
# 

```

That's Greek to me ... no working leases??

Any help would be much appreciated!

-- AF

---

