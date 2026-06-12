---
title: "Accessing my RAID devices"
date: 2009-06-01
forum: General Help
---

### Post by Keldek on 2009-06-01
Hello, back again...

Just got back to using Ubuntu after trying openSUSE for a while and now I'm stuck trying to access my raid drives...

Motherboard: MSI K9A2 Platinum
RAID device: Promise Fastrak TX2650 (onboard)
RAID Type: JBOD (2 drives)
Ubuntu version: 8.10 x86_64 (Gnome)

Now, Ubuntu is recognizing my onboard controller...

```

~$ lspci -vv -nn

03:00.0 RAID bus controller [0104]: Promise Technology, Inc. PDC42819 [FastTrak TX2650/TX4650] [105a:3f20]
	Subsystem: Micro-Star International Co., Ltd. Device [1462:3716]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR+ <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 15
	Region 0: I/O ports at d800 [size=128]
	Region 2: I/O ports at d400 [size=256]
	Region 3: Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
	Region 4: Memory at feac0000 (32-bit, non-prefetchable) [size=128K]
	Region 5: Memory at feafc000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>

``` 

But I'm not sure how to access it. I've visited Promises site, but the drivers they provide are way outdated and I haven't been able to compile them properly so now I'm stuck.

Being that the device is being recognized, do I really need the drivers? Every other device listed in lspci are all working properly, so maybe I'm just not going about accessing the device properly?

Any insight would be greatly appreciated.

---

### Post by ronparent on 2009-06-01
Try installing dmraid and using the command **dmraid -r** from live cd. This will tell you if your raid is recognized by dmraid. If it is you can access your raid drives thriugh the dmraid utility. Installing ubuntu 9.04 to the raid may be another matter. See this site for installing to a fakeraid: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Those instructions will work for 8.04, 8.10. I'm not so sure for 9.04 however.

---

