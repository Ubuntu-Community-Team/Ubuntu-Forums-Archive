---
title: "Random User Logged Off :mad:"
date: 2012-07-06
forum: Desktop Environments
---

### Post by devilcode on 2012-07-06
Hi all, :mad:

Any one else getting an issue where they are suddenly and randomly but violently logged off with no warning, loosing all and any open applications or work ?

You then get presented with the login screen. You can then log back in ....until the next random log out event.

Any ideas?

Thanks,

PC Details:
Distributor ID: Ubuntu
Description: Ubuntu 12.04 LTS
Release: 12.04
Codename: precise

Linux 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux
Architecture: i686
CPU op-mode(s): 32-bit, 64-bit
Byte Order: Little Endian
CPU(s): 4
On-line CPU(s) list: 0-3
Thread(s) per core: 1
Core(s) per socket: 4
Socket(s): 1
Vendor ID: GenuineIntel
CPU family: 6
Model: 30
Stepping: 5
CPU MHz: 2792.856
BogoMIPS: 5585.69
Virtualisation: VT-x
L1d cache: 32K
L1i cache: 32K
L2 cache: 256K
L3 cache: 8192K

---

### Post by Cheesehead on 2012-07-06
> **devilcode said:**
> they are suddenly and randomly but violently logged off with no warning, loosing all and any open applications or work ?

You then get presented with the login screen. You can then log back in ....until the next random log out event.

It's not random. And it's not common. A process called "the X server" controls the video signal. When the X server crashes (or another process terminates it), it automatically restarts. Your session is lost at the crash. The end of that restart is reloading the login screen. I've gone years without an X crash.

There are two ways to solve the problem: 1) Get a backtrace and file a bug report, or 2) Try to isolate which process of yours is causing the crash without getting a backtrace.

Getting a backtrace is the best way to really solve the problem permanently. The backtrace tells a developer exactly what happened and why. But it's also the most technically challenging. It's explained in [https://wiki.ubuntu.com/X/Backtracing](https://wiki.ubuntu.com/X/Backtracing) .

If the process explained in that link is too scary, then try to narrow down the list of possibilities. What applications are you running when the crash occurs? Does it happen more often with one application? Are you running the correct drivers for your video card?  Does your system run hot? When did the problem begin? Is there anything you can do that reliably causes a crash?

Check your /var/log/syslog and /var/log/dmesg right after a crash for clues, too.

---

### Post by black veils on 2012-07-07
i get the same thing, only since 12.04. it doesnt happen often, so somehow i have not lost anything important when the time occurs, yet.

---

