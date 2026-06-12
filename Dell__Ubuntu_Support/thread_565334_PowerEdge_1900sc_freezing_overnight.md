---
title: "PowerEdge 1900sc freezing overnight"
date: 2007-10-02
forum: Dell  Ubuntu Support
---

### Post by MxGB on 2007-10-02
Hello,

I'm having problems with a Poweredge 1900sc server recently converted to Ubuntu server 6.06 from Win2k. Although the system is performing beyond expectations, twice now it has simply frozen overnight.

Looking at the system/kernel logs hasn't revealed anything, there is nothing out of the ordinary at around or just before the crash time, and nothing else recorded in the logs until the machine is rebooted the next morning. Symptoms are that the local monitor goes blank, keyboard and mouse appear to be dead, no TCP services are working, yet the system does reply to pings.

Where else can I look other than the logs in /var/log to try and find out what is causing this?

---

### Post by MxGB on 2007-10-11
Thanks to advice from  Ivan Krsti&#263; of the ubuntu-server mailing list, the likely cause of this problem has been found to be the APIC controller of the cpu/motherboard. Further examination revealed this entry in the kernel log:```
MP-BIOS bug: 8254 timer not connected to IO-APIC
```Passing the 'noapic' and 'nolapic' options to the kernel at boot time seems to have made it go away.

---

