---
title: "Help with joystick"
date: 2006-01-09
forum: General Help
---

### Post by beniwtv on 2006-01-09
Hi there.

When I modprobe the ns558 module for joystick, it detects just an ISA gameport.
So, I have to rmmod and re-modprobe the module to detect the PnP gameport.

Has this module a parameter to tell it directly to use PnP?

Thanks.

---

### Post by pjbgravely on 2006-04-03
I believe it would go in 

/etc/modprobe.d/alsa-base

I am not 100% sure but it can't hurt to try.

Paul

---

### Post by beniwtv on 2006-06-15
UPDATE: Works now great with Dapper

---

