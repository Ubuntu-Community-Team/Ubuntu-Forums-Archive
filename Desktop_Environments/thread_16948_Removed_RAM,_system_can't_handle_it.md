---
title: "Removed RAM, system can't handle it"
date: 2005-02-24
forum: Desktop Environments
---

### Post by Dustin Wyatt on 2005-02-24
When I installed Ubuntu, I had 384MB of RAM.  After awhile I started having strange lock-up issues.  I eventually narrowed the problem down to a 256MB stick having problems so I removed it, leaving me with 128MB.

The problem is that after awhile "Used memory" in System Monitor goes up to close to 120MB and the system becomes so sluggish as to become unusable.

When I first boot it's using around 84MB.  Even if I do nothing on the system, several hours later it's back up to close to 120MB and sluggish as can be.

I can't seem to pinpoint any process that is hogging resources.

Any ideas?

---

### Post by bored2k on 2005-02-24
Did you try making a big virtual memory ? like, lets say... 1gb of virtual memory ?

i have seen ubie work on 128 with vr memory

---

### Post by poofyhairguy on 2005-02-24
[QUOTE=Dustin Wyatt]When I installed Ubuntu, I had 384MB of RAM.  After awhile I started having strange lock-up issues.  I eventually narrowed the problem down to a 256MB stick having problems so I removed it, leaving me with 128MB.

The problem is that after awhile "Used memory" in System Monitor goes up to close to 120MB and the system becomes so sluggish as to become unusable.

When I first boot it's using around 84MB.  Even if I do nothing on the system, several hours later it's back up to close to 120MB and sluggish as can be.

I can't seem to pinpoint any process that is hogging resources.

Any ideas?[/QUOTE]


New RAM (its cheap, even for decent stuff). XFCE till then.

---

### Post by az on 2005-02-25
[http://rick.vanrein.org/linux/badram/](http://rick.vanrein.org/linux/badram/)

Quote:
BadRAM: Linux kernel support for broken RAM modules
Summary: This page proposes an approach to support RAMs with defective addresses, This may open interesting business perspectives, where those RAMs can be sold under a white label for less money rather than discarded of without any profit. 
Objective of the project
My objective is to patch the Linux kernel in such a way that it can handle defective RAM modules. With defective RAM, I mean RAM which has some bits wrong at some (known) addresses. Normally, such RAM is considered useless and thrown away; the larger RAMs get, the higher the chances of failing addresses. With ever growing RAM sizes, it would therefore be pleasant to have an alternative to discarding of defective RAM chips.

---

