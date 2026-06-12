---
title: "how to: configure acpi? did I miss the memo?"
date: 2006-07-04
forum: Desktop Environments
---

### Post by 11hjpphty76lkjj on 2006-07-04
I've been looking all over can't find out how to configure acpi.......direction?

I want to change this:
~$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no

to this:
~$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         no <b>(not sure what this does?</b>


Thanks for looking.

A

---

