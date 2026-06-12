---
title: "VirtualBox Error with VT-x/AMD-V after suspend"
date: 2009-04-26
forum: Desktop Environments
---

### Post by graysky on 2009-04-26
When I suspend Intrepid-amd64 box and then awaken it again,  VBox doesn't run my 64-bit guest VM and gives this error:
```
VT-x/AMD-V hardware acceleration has been enabled, but is not operational.  Your 64-bit guest will fail to detect a 64-bit CPU and will not be able to boot.
Please ensure that you have enabled VT-x/AMD-V properly in the BIOS of your host computer.
```
I rebooted and entered my BIOS.  All my virtualization options are set to enable.  If I **totally power down my system**, then boot into Linux, the problem is gone and the 64-bit VM works just fine.  If I just reboot, the problem is **not** solved and the 64-bit VM does not work giving that error.  This problem starts when the machine gets suspended and then awakened. Upon waking up, the symptoms I described above occur and they survive a reboot!  Again, the only cure seems to be a power down then startup again (cold boot).

Can anyone suggest why this might be happening? Are they any logs I can look into to help trouble-shoot?

Can anyone else out there who has a 64-bit VM give this a try and report back?

1) Verify that the 64-bit VM works
2) Suspend your host machine then wake it back up
3) Try to run your 64-bit VM again and see if you get the same result I do

---

### Post by graysky on 2009-04-26
UPDATE: I just booted into Windows XP x64 edition and repeated this bug so it's probably not a Linux issue, it's either a problem with VBox, or with my system/Motherboard (BIOS).

Can anyone else out there who has a 64-bit VM (Windows, or Linux host) please give this a try and report back?

1) Verify that the 64-bit VM works
2) Suspend your host machine then wake it back up
3) Try to run your 64-bit VM again and see if you get the same result I do

---

### Post by danstiner on 2009-10-26
I have this issue also in Windows 7 64bit with any VT-x vm's after resuming from a suspend state.

Using a eVGA 680i LT mobo with a E6750 Intel Core 2 Duo

Might attempt a bios update sometime to see if that fixes it, but I'm none to hopeful.

---

### Post by FirefoxRocks on 2011-03-10
This problem can also be confirmed on Windows 7 64-bit Host, CPU is Intel Core 2 Duo E8400.

---

