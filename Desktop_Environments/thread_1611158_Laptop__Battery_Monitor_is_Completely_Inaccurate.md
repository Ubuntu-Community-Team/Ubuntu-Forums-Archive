---
title: "Laptop  Battery Monitor is Completely Inaccurate"
date: 2010-11-01
forum: Desktop Environments
---

### Post by Falafelkart on 2010-11-01
I just did a fresh install of Ubuntu 10.10 (from version 9.1 I believe) and now the power management program is totally out of whack.  It originally said "estimating..." when I clicked on the icon in the panel, which is a bug many people seem to have.  I used Brian Roger's PPA from launchpad.net and that changed the problem.  Now I see a percentage when I click the icon, but its at 0.1% and refuses to charge.  I know this isn't a hardware problem because everything worked fine before the install.

This is not something I can ignore, because the computer thinks the battery's charge is so low, that if I unplug it, the computer shuts off....

I'm fairly confident this is a bug related to 10.10, but couldn't find someone having quite the same issue.  FYI my laptop is an eeePC 901 with an AtomN270 processor.

Please help!  I'm new to Linux, so please go easy!

---

### Post by Remlapw on 2010-11-01
I've got a similar problem.  Mine will seem to charge very slowly to about 5% and then suddenly jump to 100% where it doesn't charge anymore.  However when unplugged I have only 10 minutes or so of battery life.  I'm looking for a fix for the laptop battery charging fix aswell.

---

### Post by Falafelkart on 2010-11-02
Yeah, I get notifications that are all over the place... today it told me 9:05 until charged, then 0:35 until charged about 10 minutes later. Pretty frustrating...

---

### Post by glynallinson on 2010-11-02
I'm also experiencing this power managment problem with 10.10 and 10.04. At one point I got so fed up I went back to XP, but alass I missed my beloved Ubuntu. Hope someone finds a solution soon.

---

### Post by KdotJ on 2010-11-02
I have the same trouble. I have ubuntu on my laptop and I have it plugged in 24/7 so I don't care, but my netbook however, I use for uni so I need to have it running off battery. Lucid and maverick are a joke with battery power management. It would be fully charged and then once unplugged, shut itself down after about 15mins with "critical battery level". I ended up switching distro on my netbook, now it lasts a good 3 hours

---

### Post by sedawk on 2010-11-02
I think the relevant data files on the system are located
at /proc/acpi/battery/BAT0/ and you can have a look yourself
from a terminal with
```

cat /proc/acpi/battery/BAT0/state
cat /proc/acpi/battery/BAT0/info

```
You can check if the numbers there are okay, e.g.
if the remaining capacity behaves correctly, e.g. it
should grow smoothly when charging and should shrink
smoothly when the power cord is unplugged.

Most likely the numbers there are incorrect, e.g. the
remaining capacity does big jumps and therefore
the tools freak out.

I recommend to dump the kernel message buffer into a file
after a fresh boot:
```

dmesg >dmesg.out

```
and then check for messages about acpi/ACPI in that file,
e.g. warnings or errors.

( I have a quirky laptop that needs acpi=force if I want
WLAN but then USB will not work and vice versa ).
There is a number of acpi boot parameters you can try to
make battery "counters" work again.
It heavily depends on your hardware/bios, so check out for
users with the same hardware.

---

