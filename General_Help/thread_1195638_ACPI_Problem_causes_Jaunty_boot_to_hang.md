---
title: "ACPI Problem causes Jaunty boot to hang"
date: 2009-06-24
forum: General Help
---

### Post by waterbucket17 on 2009-06-24
Installed Ubuntu 9.04 on a Motion Computing M1400 tablet.

It boots fine if I disable acpi by using acpi=off, but otherwise it freezes during boot. Using apm is okay for the most part, but I'm having some some problems with it (mostly that it refuses to see the battery). Since the specs claim the BIOS is "ACPI 1.1 Compliant" it'd be nice to get it working.

I've tried several acpi related boot options and have even corrected the errors and warnings in the DSDT, but to no avail.

When the boot freezes it's always in the same place. Keyboard becomes unresponsive and I have to kill the power to restart. I can't think of any way to get at dmesg after this happens (am I missing something here?), so I took a video recording of the boot process and attached the only three legible screenshots from it.

Also attached is output from dmesg after a successful boot with acpi=off, if it's at all helpful.

At this point I'm out of ideas, so any suggestions appreciated!
wb17

---

### Post by Favux on 2009-06-24
Hi waterbucket17,

You might want to talk to priegog and company.  Start with post #46 here:  [http://ubuntuforums.org/showthread.php?t=796359&page=5](http://ubuntuforums.org/showthread.php?t=796359&page=5)  Probably be helpful to join them on the bug report.

I hope this is useful.

---

### Post by waterbucket17 on 2009-06-25
It was, thank you.

For future reference, bug report is here:
[https://bugs.launchpad.net/bugs/386272](https://bugs.launchpad.net/bugs/386272)

---

