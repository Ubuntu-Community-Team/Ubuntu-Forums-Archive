---
title: "XFCE4 Battery Monitor"
date: 2005-05-26
forum: Desktop Environments
---

### Post by xethm55 on 2005-05-26
I have a laptop that i occasionally use without it being plugged in.  I have grown fond of XFCE in the past weeks since using it.  The only problem that i am having with it is the battery monitor.  The monitor itself works, however it makes the Xfce panel run at a very slow rate.  it takes about 2 minutes for it to acknowlege that i have my mouse over it (it is set to autohide, personal preference).  When i remove the battery monitor it works fine.  I was wondering what i am doing wrong.  Is there a way to get it to run faster with the battery monitor working?

Thanks,
Xethm55

---

### Post by kb00heda on 2005-05-26
I use XFCE on a laptop too, but have not experienced that kind of problem. Is it the same when running on AC, or does the slow panel follow from not being plugged in?

I don't know if this is an alternative for you, but omitting the battery monitor from the panel, you could always type

```
acpi -V
```
in a terminal to see, e.g., the battery current status. I get

kb00heda@ubuntu:~$ acpi -V
Battery 1: charged, 100%
Thermal 1: ok, 53.0 degrees C
AC Adapter 1: on-line

when running connected. Either use "acpi", or, if that doesn't work, "apm" instead.

---

### Post by xethm55 on 2005-05-26
Thanks, that helped, to the extent that i am able to see what i have left battery wise.  The problem persists when i have it plugged in as well.  I am not that sure why.

-Xethm55

---

