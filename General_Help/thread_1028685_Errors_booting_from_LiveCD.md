---
title: "Errors booting from LiveCD"
date: 2009-01-02
forum: General Help
---

### Post by gausie on 2009-01-02
Hi all

When loading from LiveCD, I get

> "BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)

(initramfs) [ 69.592268 ] end_request: I/O error, dev sr0, sector 1432224
[ 69.592316 ] Buffer I/O error on device sr0, logical block 358056

I get the feeling formatting the box and installing from fresh, will fix it, but I don't want to risk having a non-working box.

Can anyone tell me how to fix this?

Cheers, Gausie

---

### Post by laxwrestler on 2009-01-02
I had a similar problem when trying to install ubuntu from the live cd.

The solution for me was to hit f6 and add the option "pci=nomsi". No idea really what this solves or what the problem was.  I had just built the computer and it was an AMD64 so I figured it was some sort of hardware problem.  Hope that helps for you.

---

### Post by gausie on 2009-01-02
it worked!
i talk to you now from linux mint, and im happy with my decision :-)

---

### Post by laxwrestler on 2009-01-02
glad i could help :)

---

