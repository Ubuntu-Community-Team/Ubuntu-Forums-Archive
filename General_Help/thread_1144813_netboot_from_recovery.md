---
title: "netboot from recovery?"
date: 2009-05-01
forum: General Help
---

### Post by m3bik on 2009-05-01
I received a server today, by UPS, that I bought on eBay. The server does not have a CDROM or floppy drive.

The server has Ubuntu installed already- I'm surprised anyone would mail a computer of any kind without formatting... None the less, I don't have the login information, but I can get into the recovery mode and into root shell with networking. Is there anyway I can use this to format and load my own OS into the server, like a netboot?

The server can not boot from usb thumbdrives either (I've already tried).

I mean, like maybe download a file then run it? Anything?

---

### Post by blazemore on 2009-05-01
Why don't you just use an IDE or SATA CD drive from an old system, or borrow one from a current system?

---

### Post by geirha on 2009-05-01
If the BIOS supports PXE boot, then you can install an OS over the network, yes. Try searching for "install <wanted OS> over network with PXE" in your favorite search engine, and there'll probably be lots of guides.

---

