---
title: "[SOLVED] Failed to install Ubuntu"
date: 2007-07-09
forum: Desktop Environments
---

### Post by arashiko28 on 2007-07-09
Due to a voltage problem, my laptop display is damaged along with several other parts as the DVD and batt. So I decided to undust the old and trusty desktop, problem: It is reaaally OLD. If i'm not mistaken have it since 98-99 with no hardware importants changes. Is has an Intel Celeron processor 701MHz and 256MB of RAM.

I inserted the ubuntu cd and restarted, it started ok, but it froce, it started to show some errors on atapi something and retry and failed, it remained there for about 15 minutes, I wrote a command to stop and shut down. Does this means that the good old Bob, (I named it Bob), does not support Ubuntu???:confused:

---

### Post by taurus on 2007-07-09
Have you tried using the alternate CD of Xubuntu?  It works good for older computers.

[http://www.xubuntu.org](http://www.xubuntu.org)

---

### Post by arashiko28 on 2007-07-09
While Xubuntu is downloading, i kept trying to install Ubuntu. This is what appears after load the Linux Kernel:

BustyBox v1.1.3 (Debian 1:1.1.3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) [     39.816000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[     39.816000] ata1.01: (BMDMA stat 0x65)
[     39.816000] ata1.01: cdm a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 254 in
[     69.832000] ata1: port failed to respond (30 secs, Status 0xd8)
[     70.152000] ata1.01: revalidation failed (errno=-2)
[   105.668000] ata1.01:  exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[   105.668000] ata1.01: cdm a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x12 data 254 in

Goes on and nothing happens... it is still

---

### Post by arashiko28 on 2007-07-20
Problem solved, the problem was the PC, got Xubuntu

---

