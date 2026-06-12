---
title: "Xubuntu failing to load after BIOS upgrade"
date: 2009-01-06
forum: General Help
---

### Post by miocene on 2009-01-06
My Laptop specs:

*Dell inspiron 1100*
Celeron 2.00GHz
256MB RAM (Only 128MB recognised)
40GB HDD
Integrated Graphics

For some reason that I don't know only one of my DIMM slots for the RAM is working on my laptop so I'm having to cope at the moment with 128MB.
This, as you'd expect, has made Xubuntu extremely slow (even slower than XP).
So I have ordered a 512MB stick to replace the working 128MB stick.

I read online that the Dell Inspiron 1100 would need a BIOS upgrade to see this amount of RAM so I went and flashed the BIOS with a bootable CD up to A32 (the latest version) while I still await delivery of the new RAM.

Now when I boot into Xubuntu, the loading screen appears and completes and just before the login screen appears the screen goes blank and the computer is unresponsive.

Is this because of a lack of memory (I know 128MB is cutting it fine for Xubuntu), as such the RAM upgrade should fix it, or is there someone worse going on?

PS The BIOS upgrade went fine.

---

### Post by blazemore on 2009-01-06
Why did you update your BIOS?
The best you can hope from your BIOS is that you don't notice it at all.
My guess is that you weren't aiming for any hardware upgrades which were only supported by a new BIOS version, you just thought, "ooh, 116 is a bigger number than 108, I'll use that one"

MESSING WITH YOUR BIOS CAN PHYSICALLY BREAK YOUR HARDWARE

It's not like tinkering with the OS, where if all goes wrong you can simply reinstall. Buggering about with firmware can cause all sorts of issues down the line with software not used to the new configuration.

Obviously the BIOS "upgrade" DIDN'T go fine, or you wouldn't be having this problem.

---

### Post by miocene on 2009-01-06
I updated it because to install the new RAM that is arriving in the post the old BIOS cannot recognise 512MB sticks.

I think the update did go fine because it completes "post" no problems and goes to the Xubuntu load screen. It is only after the load screen that it fails (just after the cursor appears).
I'm hoping its a lack-of-memory problem.

---

### Post by blazemore on 2009-01-06
Have you tried booting into recovery mode, and running everything on that list?

---

### Post by miocene on 2009-01-06
Booting via recovery mode worked!
Its still slow but I'm hoping the 512MB RAM upgrade will speed it up a bit.
cheers

---

### Post by boof1988 on 2009-01-06
> **blazemore said:**
> Why did you update your BIOS?
The best you can hope from your BIOS is that you don't notice it at all.
My guess is that you weren't aiming for any hardware upgrades which were only supported by a new BIOS version, you just thought, "ooh, 116 is a bigger number than 108, I'll use that one"

MESSING WITH YOUR BIOS CAN PHYSICALLY BREAK YOUR HARDWARE

It's not like tinkering with the OS, where if all goes wrong you can simply reinstall. Buggering about with firmware can cause all sorts of issues down the line with software not used to the new configuration.

Obviously the BIOS "upgrade" DIDN'T go fine, or you wouldn't be having this problem.

 @blazemore,

Did you read the OP?????

[SIZE="3"]PLEASE READ THE OP BEFORE PREACHING.[/SIZE]

And be kind. :)

Edit:

@Miocene,

I'm glad your machine is running now.

---

