---
title: "Bad shutdown on Karmic"
date: 2010-05-03
forum: Desktop Environments
---

### Post by Kermit524 on 2010-05-03
Hi, After having installing the last recommended updates on my system (Karmic), when shutting  down - the system won't turn off, but instead - there is a screen full of messages.
I have copied down some of these messages and it looks like this:
c0000000d
[4107.924020]
78 hrtimer_cpu
38 notifier_call_chh
99 random_notifier
_cpu_down
disable_nonboot_
acpi
kernel pwer(?) off

This goes on like this for quite a while. Last message is:
4107.927476]---- end trace]

After that - the system freezes. Only way to release it is by pressing down the off button for couple of seconds. Then the machine turns off, and normally everything is fine when re-booted.

I should say that I have long ago disabled the "quiet hash" on my menu.lst (Grub1), and up untill now - no problems at that.

Any idea what this might be or how can it be fixed?

Many thanks in advance,
Michal

---

