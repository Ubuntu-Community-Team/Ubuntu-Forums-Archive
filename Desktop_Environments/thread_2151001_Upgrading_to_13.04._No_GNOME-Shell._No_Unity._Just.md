---
title: "Upgrading to 13.04. No GNOME-Shell. No Unity. Just GNOME Fallback."
date: 2013-06-03
forum: Desktop Environments
---

### Post by salman123 on 2013-06-03
Hello Everyone.

I had Ubuntu 12.10 working on my machine perfectly, having GNOME and Unity altogether, and I decided to move to 13.04. I disabled PPAs and changed the contents of
```

/etc/apt/sources.list

```
and replaced *quantal* with *raring*.

Now after upgrading the system, Unity 7 does not start. I can remember that it showed me an error with *Compiz* just one time after first log in. And after that when I log in my account, I can just see the background and nothing more. Right-click works on desktop background and I can start terminal using *Alt+Ctrl+T*.

After searching the web I found somewhere that we should try this code to correct Unity 7.
```

$ dconf reset -f /org/compiz/
$ setsid unity

```

And After all, I can use neither GNOME Shell 3.6 and Unity 7. Just GNOME Fallback.

PS1: I haven't added PPA of GNOME 3.
PS 2: lspci
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1c.7 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6400M/7400M Series]
24:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 30)
24:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 30)
24:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 30)
25:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
26:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
27:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

```

---

### Post by salman123 on 2013-06-06
Can't anyone help me?

---

