---
title: "Kubuntu Natty Performance Issues"
date: 2011-10-14
forum: Desktop Environments
---

### Post by mykes on 2011-10-14
I am seeing Kubuntu x64 performing 1/3 as fast running native on my hardware vs. running in a VirtualBox VM on the same hardware.  This makes no sense to me.  I have done some benchmarking of the kinds of work I do on another machine and found the opposite to be true (1/3 the performance IN a VM).

I'm doing a large MySQL data conversion and import.  Simple import of the database using 

zcat db.sql.gz | mysql db  

is 1/3 as fast running natively on the hardware.

I've tuned MySQL to use the full 8G of my machine.   The VM is configured with 2G of RAM.

I check with cpufreq-info and it says my 4 cores are at full 2.80GHz frequency while the import is going on.

Aside from the VM vs. bare metal difference, KUbuntu is running on its own dedicated drive.  Windows boots off a SATA Raptor 10K RPM drive, while the KUbuntu drive is a SAMSUNG JD253GJ 250G drive.  I don't notice the disk is particularly slow.

While importing the database, I run mytop and see a consistent 2 qps.

When I run my own custom import scripts (to convert the data), I see things that take 35 seconds on the native hardware take 10 seconds in the virtual machine.

What gives?

---

