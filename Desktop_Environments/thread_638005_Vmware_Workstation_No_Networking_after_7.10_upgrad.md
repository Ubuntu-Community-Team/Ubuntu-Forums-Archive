---
title: "Vmware Workstation No Networking after 7.10 upgrade"
date: 2007-12-11
forum: Desktop Environments
---

### Post by archivalbackup on 2007-12-11
I upgraded from Fiesty (where everything was working) and installed the latest version of VMware Workstation. I went through the network config again and assigned my network adapters correctly; however now none of my VM's get any network access through my bridged wireless or wired network interfaces. 

Help?

Edit: Gateway talbet laptop, intel 3945 wireless card w/ restricted drivers, broadcom gig Ethernet.

---

### Post by archivalbackup on 2007-12-12
Ok, I re-ran the config again, and the Ethernet network device does work, the wireless device does not work. 

Anyway I could make a virtual interface that would connect to the wireless card and try that?

---

### Post by archivalbackup on 2007-12-12
Dmesg output: (eth2 is my wireless adapter)

176462.028000 bridge-eth1: enabled promiscuous mode
176462.028000 /dev/vmnet: port on hub 3 successfully opened
176464.000000 device eth2 left promiscuous mode
176464.000000 audit(1197412647.928:120): dev=eth2 prom=0 old_prom=256 auid=4294967295
176464.000000 bridge-eth2: disabled promiscuous mode
176464.000000 /dev/vmnet: open called by PID 16998 (vmware-vmx)
176464.000000 device eth2 entered promiscuous mode
176464.000000 audit(1197412647.928:121): dev=eth2 prom=256 old_prom=0 auid=4294967295
176464.000000 bridge-eth2: enabled promiscuous mode
176464.000000 /dev/vmnet: port on hub 2 successfully opened

---

### Post by archivalbackup on 2007-12-12
T-Ubuntu:~/WirelessProfiles$ ps ax|grep -i bridge
5848 ? Ss 0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-0.pid /dev/vmnet0 eth1:avah
5859 ? Ss 0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-2.pid /dev/vmnet2 eth2
5865 ? Ss 0:00 /usr/bin/vmnet-bridge -d /var/run/vmnet-bridge-3.pid /dev/vmnet3 eth1
12773 pts/0 S+ 0:00 grep -i bridge

6.0.2 build-59824

---

