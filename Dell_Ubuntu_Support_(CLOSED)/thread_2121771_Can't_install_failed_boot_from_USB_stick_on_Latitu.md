---
title: "Can't install: failed boot from USB stick on Latitude E6410"
date: 2013-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ceverett on 2013-03-03
I don't think this has anything to do with booting from USB.

This machine fan just fine with 10.10 for years, though I had to do it with setmode turned off in the grub boot line.

But I just installed a new 1TB drive on the lappie (I'm a DJ and been chronically short of drive space for years), so I thought I would upgrade.

I've tried several 32 and 64 bit variants of ubuntu : ubuntu 12.10, lubuntu 12.10, mint 14 in both Cinnamon and MATE flavors.

To date all have have failed.  Because Mint does its own thing with the ISO, starting Cinnamon in the compatibility mode show an error where it fails on the step "starting load fallback graphics devices".

So I believe the issue is with Xwindows.

Anyone got a clue for me?

---

### Post by gordintoronto on 2013-03-03
What is the video adapter? lspci | grep vga

---

### Post by ceverett on 2013-03-03
```
root@johannes:/home/ceverett# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

---

### Post by gerrman97 on 2013-03-28
what kind of hdd was it? sometimes the upgrade of size in hdds will cause the fan to overheat. i have done the same with my Dell Latitude E6400 and my other E6410, and i had problems at first. the fan was spinning up way too much, and when it wasnt on, the laptop was REALLY hot. id try running with a cooling pad. or, try formatting hdd when booting from disc/usb and installing from there. those Latitiudes USB hubs are pretty diffucult, even with windows installed.

---

