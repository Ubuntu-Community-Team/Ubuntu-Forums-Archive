---
title: "How to stop/start a program when notebook goes battery/ac?"
date: 2010-10-23
forum: Desktop Environments
---

### Post by amastronardi on 2010-10-23
I need to stop a program when notebook goes on battery and start it when using AC. I'm using 10.10 netbook edition.

Thanks,
AM

---

### Post by sikander3786 on 2010-10-23
For the time being, until someone doing that himself jumps in, you can go through these for some initial info.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

[http://ubuntuforums.org/showthread.php?t=1255377](http://ubuntuforums.org/showthread.php?t=1255377)

---

### Post by amastronardi on 2010-10-23
> **sikander3786 said:**
> [http://ubuntuforums.org/showthread.php?t=1255377](http://ubuntuforums.org/showthread.php?t=1255377)

Thanks for the reply. However, it seems like in Maverick ACPI is managed in a different way as 
```
/etc/acpi/battery.d/your_script.sh
```
and 
```
/etc/acpi/ac.d/your_script.sh
```
don't exist.

Looks like it now manages *events* but can't understand yet how to manage those events.

Cheers,
AM

---

