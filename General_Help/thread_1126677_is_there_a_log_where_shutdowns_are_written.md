---
title: "is there a log where shutdowns are written?"
date: 2009-04-15
forum: General Help
---

### Post by chriskin on 2009-04-15
i would like to know when my computer turned off, is there a log where i can find this? 
:)

:popcorn:

---

### Post by f8l_0e on 2009-04-15
In the terminal, use the following command:

last -x| less

This will give you recent the recent reboot / shutdown history.  This only works if someone send a command to reboot, so you can't use this to determine if there was a power outage or if someone held the power switch to turn the system off.

---

### Post by chriskin on 2009-04-16
thank you :) 

:D

---

