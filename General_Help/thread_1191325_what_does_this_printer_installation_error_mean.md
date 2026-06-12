---
title: "what does this printer installation error mean?"
date: 2009-06-18
forum: General Help
---

### Post by ymp on 2009-06-18
Tried to reinstall a Brothers HL 2040 printer which Ubuntu 9.04 won't connect with since upgrading from 8.10.
Through CUPS web interface I receive the following error message when I try to reinstall the printer:

Error:

    Bad device-uri "ipp://fe80::a10:74ff:fe18:b5ca:631/printers/HL-2040_series"!

Advice what to next appreciated!;)

---

### Post by redmk2 on 2009-06-18
> **ymp said:**
> Tried to reinstall a Brothers HL 2040 printer which Ubuntu 9.04 won't connect with since upgrading from 8.10.
Through CUPS web interface I receive the following error message when I try to reinstall the printer:

Error:

    Bad device-uri "ipp://fe80::a10:74ff:fe18:b5ca:631/printers/HL-2040_series"!

Advice what to next appreciated!;)

I believe the IP address noted is ipv6.  Are you using ipv6 in your network?  If not then use the ipv4 address.  An example wold be: [COLOR="Red"]192.168.0.12:631[/COLOR].

I don't know your setup so this is a best guess.

---

