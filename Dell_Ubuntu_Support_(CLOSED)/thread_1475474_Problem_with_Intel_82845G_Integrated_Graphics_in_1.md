---
title: "Problem with Intel 82845G Integrated Graphics in 10.4"
date: 2010-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by oyok2112 on 2010-05-06
I finally upgraded to 10.4 today (well actually did a fresh install, but I've been using Ubuntu for years now).  I'm using an nVidia GeForceFX 5500 card on my old Dimension 2400, and had problems in the past enabling Compiz because, for some reason, Ubuntu still detects the Intel integrated graphics card which is blacklisted.

Now, in past releases all I had to do was run Compiz with the 'SKIP_CHECK=yes' option, and I had my translucent terminal and desktop cube and all that good stuff.  However, I did some research and found that the 'SKIP_CHECK' option won't work in 10.4 like it used to.  

I would gladly just disable the Intel on-board graphics in the BIOS, but that's frustratingly not an option.  I removed the Intel graphics drivers in Synaptic, and blacklisted 'intel_agp' in the modprobe.d/blacklist.conf file.  The Intel driver is still showing up in lspci.  Speaking of, here's the obligatory lspci printout:

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
01:04.0 Network controller: RaLink RT2760 Wireless 802.11n 1T/2R Cardbus
01:05.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
01:06.0 Multimedia audio controller: Creative Labs SB X-Fi
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
```


And also the error message from Compiz:

```
Blacklisted PCI ID 8086:2562 detected
```

---

### Post by jtbse on 2010-05-07
Having the exact same issue.  Rebuilt my 2400 with Ubuntu 10.4, and added Nvidia GeForce 8400 GS.  But alas, compiz still finds the blacklisted Intel PCI device (even though X seems to be successfully loading the Nvidia driver).

And as you mentioned on the 2400,  we can't completely disable the onboard graphics.

So I'd really like to know how to work around this.

---

### Post by Cmain on 2010-05-18
I am having the same issue.  Any help would be greatly appreciated!

---

### Post by oyok2112 on 2010-05-18
Well hey thanks for bumping this thread, I'm glad (and kind of surprised) that I'm not the only one experiencing this.  

I'll just reiterate here since I'm not sure I made it clear in my first post:  The video card I'm actually using (a.k.a. the one with a monitor plugged into it) is perfectly capable of running Compiz, I know since I used it for two years.  So I understand that perhaps the SKIP_CHECK option could have been used irresponsibly, but in cases like mine it was a saving grace.  Anyway, I'll keep looking in my spare time and post anything I find if something works.

---

### Post by jtbse on 2010-05-18
I found a workaround for this problem in this thread:

[http://ubuntuforums.org/showthread.php?t=1467202](http://ubuntuforums.org/showthread.php?t=1467202)

The workaround by zpletan in that thread takes care of the issue.  Involves running ghex on the compiz binary and zapping the string that checks the blacklist for the Intel on-board graphics.

But if you try it, be careful!!   The first time I did it, I managed to break compiz somehow.  But second time's a charm, as they say.  I'm now getting my desktop effects! Would advise backing up the binary before trying to edit it.

---

### Post by Cmain on 2010-05-18
Thanks for the link.  Worked for me on the first try.

---

### Post by oyok2112 on 2010-05-19
Yes!  Marked this one as solved!  Thanks everyone!

---

