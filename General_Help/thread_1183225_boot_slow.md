---
title: "boot slow"
date: 2009-06-09
forum: General Help
---

### Post by searayman on 2009-06-09
I used to boot fast i am on 9.04 with ext4 but now when I boot into ubuntu the nice ubuntu logo with loading bar loads then it goes black for a bit, and eventually I see lines and lines of text and something about battery state etc. shows up and it just wont boot smoothly.

Any ideas on what this is about?

---

### Post by searayman on 2009-06-11
anyone have any thoughts?

---

### Post by andersbk on 2009-06-11
Do a fresh reboot and log in.

Launch a terminal, and look at the kernel buffer with "dmesg".

The number in the square brackets is time. Look for a large gap in time from one line to the next, that is, your "stall" during boot. This will narrow down where the kernel is stalling during boot.

.

---

### Post by searayman on 2009-06-11
> **andersbk said:**
> Do a fresh reboot and log in.

Launch a terminal, and look at the kernel buffer with "dmesg".

The number in the square brackets is time. Look for a large gap in time from one line to the next, that is, your "stall" during boot. This will narrow down where the kernel is stalling during boot.

.

here is my output does nayoen see anythign that may be my problem:

[http://pastebin.com/f41204754](http://pastebin.com/f41204754)

---

### Post by searayman on 2009-06-12
anyonebuddy else? This is really bothering me this slow boot, cause ti was blazing for a coupel of days when i was first on ext 4

---

### Post by searayman on 2009-06-12
ok so it seems this took about 50 seconds:

 [ 26.484057] eth1: no IPv6 routers present  [ 76.804087] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x6 frozen

how can i now fix it if I am right about it takign 50 seconds?

---

### Post by andersbk on 2009-06-13
> **searayman said:**
> ok so it seems this took about 50 seconds:

 [ 26.484057] eth1: no IPv6 routers present  [ 76.804087] ata1.00: exception Emask 0x0 SAct 0x7 SErr 0x0 action 0x6 frozen

how can i now fix it if I am right about it takign 50 seconds?

Hmm...that's an ata bus error. Either an interface or cable error.
I would try disconnecting and reconnecting your sata cables first since connectors can sometimes become problematic.

.

---

### Post by searayman on 2009-06-19
> **andersbk said:**
> Hmm...that's an ata bus error. Either an interface or cable error.
I would try disconnecting and reconnecting your sata cables first since connectors can sometimes become problematic.

.

what are sata cables?

---

### Post by andersbk on 2009-06-20
> **searayman said:**
> what are sata cables?

The Serial ATA cables. The data interface cable that connects the drive to the motherboard.

The error you're getting suggests a problem with the SATA interface. Either a bad drive or cable.

.

---

### Post by soulnafein on 2009-08-16
I have the exact same problem! Did someone fix this?

---

