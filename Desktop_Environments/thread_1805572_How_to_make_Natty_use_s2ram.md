---
title: "How to make Natty use s2ram"
date: 2011-07-16
forum: Desktop Environments
---

### Post by bturrie on 2011-07-16
I just upgraded my desktop from 10.04 (Lucid) to 11.04 (Natty). One problem I'm having is that suspend isn't working on my system. The program: 

s2ram -f 

works just fine, like it did in Lucid. 

But in Lucid you could edit

/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux

to make it use s2ram for suspend. Is there a similar script that can be edited in Natty, and if so where?

---

### Post by bturrie on 2011-07-16
Odd, now suspend seems to be working???? Clearly I posted too soon.

---

### Post by bturrie on 2011-07-17
So, after more investigation:

If I invoke suspend from the Natty Top Bar Menu, it works just fine. When I push the power button it wakes up immediately as it should. I get the same results using s2ram -f

When my system suspends due to inactivity it does not work the same way. When I power back on after a inactivity suspend by power manager, it goes through the entire bios power on sequence before restoring my session.

BTW this is a desktop system. not a laptop.

---

