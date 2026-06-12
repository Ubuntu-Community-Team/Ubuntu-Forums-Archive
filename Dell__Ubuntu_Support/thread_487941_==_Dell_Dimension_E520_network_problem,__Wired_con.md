---
title: "== Dell Dimension E520 network problem,  Wired connection =="
date: 2007-06-29
forum: Dell  Ubuntu Support
---

### Post by rendezvous on 2007-06-29
Just bought a dell Dimension E520. 

After installing the Ubutu 7.04, everything is fine, except the network, it shows connected, but the speed is very slow and indicates "wired connection"

By the way, I am using AT&T DSL. I also installed a windows XP on the same machine, at first the internet speed is also slow, but after adjust the driver properties->Link Speed &Duplex -> 10Mbps/Hallf Duplex (according to dell tech support )  it works fine now.

Can anyone give me some help? what is going on? how to set up the network properly?

Thanks!!!


My Dimension 520 order details:
  
-----------------------------------------------------------------------------------------------------------------
Dimension E520n   	  Pentium® D Processor 925 with Dual Core Technology (3GHz, 800FSB)
	[222-5093]
Memory 	FREE Upgrade! 1GB Dual Channel DDR2 SDRAM at 667MHz- 2DIMMs
	[466-4504]
Keyboard 	Dell USB Keyboard
	[310-8164]
Monitor 	20 inch E207WFP Widescreen Digital Flat Panel
	[320-5092]
Video Cards 	Intel® Graphics Media Accelerator X3000
	[320-4270]
Hard Drives 	160GB Serial ATA Hard Drive (7200RPM) w/DataBurst Cache&#153;
	[341-4210]
Floppy Drive and Media Reader 	No Floppy Drive Included
	[341-4028]
Operating System 	FreeDOS&#153; included in the box, ready to install
	[420-2955]
Mouse 	Dell® 2-button USB mouse
	[310-7965]
Network Interface 	Integrated 10/100/1000 Ethernet
	[430-0412]
Modem 	No Modem
	[313-3137]
CD or DVD Drive 	16X DVD ROM Drive
	[313-4580]
[420-5781]
Sound Cards 	Integrated 7.1 Channel Audio
	[313-2758]

---

### Post by rendezvous on 2007-06-29
Additional Info: ifconfig -a
===========================================
qi@xixiaqi:~$ ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:19:D1:74:C8:AC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0xecc0 Memory:dfde0000-dfe00000 

eth0:avah Link encap:Ethernet  HWaddr 00:19:D1:74:C8:AC  
          inet addr:169.254.9.148  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Base address:0xecc0 Memory:dfde0000-dfe00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:944 (944.0 b)  TX bytes:944 (944.0 b)

---

### Post by rendezvous on 2007-06-29
I got it.

sudo mii-tool -F 10baseT-HD   

;)

---

