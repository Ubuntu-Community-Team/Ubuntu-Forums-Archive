---
title: "HEADS UP: Security Updates Kernel 2.6.15.27-k7 Broke SAMBA &amp; CXOFFICE"
date: 2006-09-28
forum: Desktop Environments
---

### Post by tagra123 on 2006-09-28
After updating, Tuesday, September 26, 2006 (mainly the updates were from dapper-security repos)

CX Office was acting strange with VB apps

Samba would no longer share a printer correctly with windows, but would share a samba printer fine with other ubuntu machines.

This Kernel 2.6.15.27-k7 seems to be the problem because the SAMBA and CUPS look like they are the same versions.

I restored from a backup and am now running Kernel  2.6.15.26-k7 and everything except CX office is working correctly again. I'm going to look over some other setting for CX Office and try to track this down.

---

