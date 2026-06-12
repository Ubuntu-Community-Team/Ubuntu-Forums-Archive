---
title: "Dell XPS Developer Edition &amp; Ubuntu 13.10 - kernel error message"
date: 2014-02-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by avastmc on 2014-02-21
Hi everyone.

Tuesday I received my new XPS 13 DE (shipped w/ 12.04 LTS) and within hours felt so inclined to try and brick it, and did succeed for some time.

After a wipe of the drive and installing 13.10 fresh, I've got everything working and I'm quite satisfied with the system overall.

One issue I am experiencing, though, wasn't present in 12.04. It's not interfering with normal operation other than slightly prolonging the boot.

With factory-installed 12.04 booting was a few seconds faster and smooth. Now, after the 'dell' logo flashes, a text screen flashes with an error, followed by a flash of a black screen with a few red lines, and then boot proceeds as anticipated.

A quick search of kern.log shows the error I saw, with surrounding text:

```
Feb 19 08:18:40 exa kernel: [    0.255921] system 00:08: [mem 0xdfa10000-0xdfa1ffff] has been reservedFeb 19 08:18:40 exa kernel: [    0.255924] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
Feb 19 08:18:40 exa kernel: [    0.256270] system 00:09: [mem 0xfe102000-0xfe102fff] has been reserved
Feb 19 08:18:40 exa kernel: [    0.256272] system 00:09: [mem 0xfe104000-0xfe104fff] has been reserved
Feb 19 08:18:40 exa kernel: [    0.256274] system 00:09: [mem 0xfe106000-0xfe106fff] has been reserved
Feb 19 08:18:40 exa kernel: [    0.256277] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
**Feb 19 08:18:40 exa kernel: [    0.258388] pnp 00:0a: unknown resource type 19 in _CRS**
**Feb 19 08:18:40 exa kernel: [    0.258390] pnp 00:0a: can't evaluate _CRS: 1**
Feb 19 08:18:40 exa kernel: [    0.258412] pnp 00:0a: Plug and Play ACPI device, IDs DLL060a PNP0c50 (active)
Feb 19 08:18:40 exa kernel: [    0.258969] pnp: PnP ACPI: found 11 devices
Feb 19 08:18:40 exa kernel: [    0.258970] ACPI: bus type PNP unregistered
Feb 19 08:18:40 exa kernel: [    0.265263] pci 0000:00:1c.0: bridge window [io  0x1000-0x0fff] to [bus 01] add_size 1000
```

I haven't used launchpad much before to file bug reports but I guess I'll be heading over there soon. I came here in hopes that some other XPS 13 owner encountered this and hopefully found a fix. An extensive internet search seemed to fall short in this specific error.

It's not terrible that a cold boot takes 6 seconds instead of 4, but I'd still like to do my part here in making these bugs known.

Thanks in advance!

---

### Post by avastmc on 2014-02-21
I'm sorry, I forgot to include";
Linux version 3.12.6-031206-generic (apw@gomeisa) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu5) ) #201312201218 SMP Fri Dec 20 17:20:06 UTC 2013

I had upgraded to this, as advised in order to fix the touchscreen.

---

