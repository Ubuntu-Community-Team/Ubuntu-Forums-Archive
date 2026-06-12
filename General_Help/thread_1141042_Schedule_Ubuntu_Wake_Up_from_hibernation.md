---
title: "Schedule Ubuntu Wake Up from hibernation"
date: 2009-04-28
forum: General Help
---

### Post by Adnanius on 2009-04-28
Like said in the title, I'd be very happy to know how to tell Ubuntu to wake up from hibernation(or Suspend?) when a scheduled task is about to start.
I'm using 9.04 now.

---

### Post by SiHa on 2009-04-29
There is a good guide here:

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

This relates specifically to MythTV / Mythbuntu, but I see no reason that it couldn't be made more generic quite easily. All you need is some way of finding out the time of the next scheduled task so it can be fed into **/proc/acpic/alarm**.

Assuming your mobo supports ACPI, that is.

---

