---
title: "Performance on my home server drops Every Day"
date: 2009-04-19
forum: General Help
---

### Post by coral on 2009-04-19
Hello!

I have a home server i setup with Ubuntu 8.10 standard with X and all that (it is sometimes used as a surf computer too, therefore i decided to include the desktop packages).

However, something has happend the last few weeks because i have to restart the machine nearly each day. When i SSH into it, it's really really slow, the load is over 100 and there is "1 zombie process". If i restart it, it works for about a day...

I haven't done anything too it the last weeks, it has just acted as a web server.

How can i find out what's slowing it down so terrible?

It's a 1.7 Ghz pentium 4 with 512 mb Ram, builtin graphics and 80 gb HDD( There is 40 gb free. ).

lspci returns:
> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VM (LOM) Ethernet Controller (rev 81)


---

### Post by dcstar on 2009-04-20
> **coral said:**
> Hello!

I have a home server i setup with Ubuntu 8.10 standard with X and all that (it is sometimes used as a surf computer too, therefore i decided to include the desktop packages).

However, something has happend the last few weeks because i have to restart the machine nearly each day. When i SSH into it, it's really really slow, the load is over 100 and there is "1 zombie process". If i restart it, it works for about a day...

I haven't done anything too it the last weeks, it has just acted as a web server.

How can i find out what's slowing it down so terrible?
........

```
man top
```

---

