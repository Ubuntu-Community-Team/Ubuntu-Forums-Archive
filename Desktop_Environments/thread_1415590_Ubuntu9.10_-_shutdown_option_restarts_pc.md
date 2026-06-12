---
title: "Ubuntu9.10 - shutdown option restarts pc"
date: 2010-02-25
forum: Desktop Environments
---

### Post by justsayraj on 2010-02-25
Hi All,

I am using ubuntu 9.10.
After installing updates in last couple of days prompted by Update Manager as security updates and recommended updates my desktop pc does not shutdown.

When using 'shutdown or halt' options my pc does not shutdown instead pc restarts to login page back.

uname -a
Linux ysrcdp-computer 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

Please help me in resolving this issue.

Thanks and Regards,
Raj.

---

### Post by booshire on 2010-02-25
> **justsayraj said:**
> Hi All,

I am using ubuntu 9.10.
After installing updates in last couple of days prompted by Update Manager as security updates and recommended updates my desktop pc does not shutdown.

When using 'shutdown or halt' options my pc does not shutdown instead pc restarts to login page back.

uname -a
Linux ysrcdp-computer 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

Please help me in resolving this issue.

Thanks and Regards,
Raj.

I have seen this problem with Windows. For me it was a hardware issue, updated the BIOS and it worked, then started failing again. Maybe look to the ACPI functions?

---

### Post by justsayraj on 2010-02-25
> **booshire said:**
> I have seen this problem with Windows. For me it was a hardware issue, updated the BIOS and it worked, then started failing again. Maybe look to the ACPI functions?

I am not using windows.  Only ubuntu 9.10 is on my PC.

I did not change any BIOS settings.

---- lshw command reports below information for firmware:

     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (07/26/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification

------

---

### Post by justsayraj on 2010-02-25
After recent updates are applied, shutdown doesn;t take more than 1 or 2 seconds.

It seems that all the processes are not being cleanly shutdown.

:confused:

---

### Post by claytonchwang on 2010-02-25
I have the same problem too after installing updates.

---

### Post by justsayraj on 2010-03-16
I see the below message when system restarts (trying to shutdown)

init: usplash main process (1638) killed by TERM signal.

---

### Post by Chame_Wizard on 2010-03-17
```
shutdown -h 0
```

---

### Post by justsayraj on 2010-03-18
> **Chame_Wizard said:**
> ```
shutdown -h 0
```

still shuts & restarts after displaying usplash error message.

---

### Post by justsayraj on 2010-03-21
The problem was resolved after changing power management options in BIOS settings

1. Wake up on PCI ; -> Disabled
     After setting this option 'shutdown' option behaved as expected.

2. In addition to the above, also disable 'Wake up on LAN'.

Hope it helps others too.

:hmm Only question is why ubuntu updates introduced this issue.

---

### Post by shields on 2012-01-17
OK -- this would be fine if you never needed Wake on Lan, but I have been using it for some time. Suddenly, I can't shut down my machine from Ubuntu. It just restarts.

I can solve this problem by taking advantage of my dual boot, going into Windows, and shutting down from there -- but that's just silly.

What's going on with Ubuntu's shutdown routine?

Any fix?

Oh -- and I am actually using Ubuntu 11.10.

---

### Post by sffvba[e0rt on 2012-01-17
*Back to sleep **old** thread.*

Best to start a new one with all the relevant information.


404

---

