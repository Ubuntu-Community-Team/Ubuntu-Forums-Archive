---
title: "how to enable automatic boot?"
date: 2006-07-20
forum: Desktop Environments
---

### Post by plato4me on 2006-07-20
My motherboard (ASUS A7N8X) has an automatic powerup option in its bios.  For example, I can shut my computer down at night and have it automatically powerup at 7am.

I'd like to be able to use this feature, but something in the ubuntu distribution prevents it from working.  (I'm using the current version of Dapper).

I thought the problem had to do with acpi staying in control of the power while the computer is down.  So I used update-rc.d to prevent /etc/init.d/acpid and /etc/init.d/acpi-utils from running at startup.  Before I initiate the shutdown process, none of the acpi modules is loaded.  ("lsmod | grep acpi" shows nothing.)

This didn't help.  The bios feature I want still doesn't work.  Question: What should I try next?  Is there something else I should disable?

What I want is to be able to shutdown normally, but in a way that lets me computer's bios bring it back up automatically at a set time.  BTW, I know this can be made to work, because I've don't it with other Linux distributions by disabling acpi in the kernel.

Suggestions?

---

### Post by Anduu on 2006-07-20
If your computer is shut down acpi shouldn't have anything to do with it...possibly you are not enabling it correctly in the BIOS?

Nothing Ubuntu can do will affect your PCs ability to auto power on.

---

### Post by plato4me on 2006-07-21
No, acpi definitely has something to do with it.  Here's the proof.

Yesterday, I created a custom kernel in which the only change to the standard kernel I made was to disable acpi entirely.  I ran that kernel, did a normal shutdown, and this morning at 7am, it worked perfectly.

I'm still puzzled.  Why wasn't removing all the acpi modules sufficient?

---

