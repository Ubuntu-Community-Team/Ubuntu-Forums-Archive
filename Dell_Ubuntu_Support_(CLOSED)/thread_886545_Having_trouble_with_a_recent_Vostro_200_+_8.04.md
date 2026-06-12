---
title: "Having trouble with a recent Vostro 200 + 8.04"
date: 2008-08-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DaAlexMax on 2008-08-11
I'm having a little bit of trouble with a Vostro 200.  It's a recent model with an Intel Pentium E2160 and Intel PRO 1000 network card (wired, not wireless).

When I started using Ubuntu, I remember running into problems where it would stumble upon attempting to find the hard drives.  It would give a couple of error messages, something along the lines of **ata1.00 revalidation failed** for a few moments and then simply drop to BusyBox.  I finally found out that there was a kernel option that I could pass: **all_generic_ide**, to fix things.  I did so, and everything worked, and has been working...up until two days ago.

Two days ago, I had to boot into Windows to run a program WINE couldn't handle.  I first started with Windows Vista, but upon waiting 10 minutes for it to log in I got tired of waiting for it, hit reset, and booted up into XP.  From there, I tested the program in XP and rebooted into Ubuntu.

Nothing.

It got stuck at 'Starting up', no ubuntu splash or anything.  I went into recovery mode and it would get stuck at a semi-random place, near a certian message that I could never remember the contents of.  After some research, I decided to make my kernel options list this: **acpi=off all_generic_ide**.

This got me past "Starting Up", but would then get stuck at disk detection again and dump me to BusyBox.  After a little more research, I changed my kernel options **acpi=off irqpoll all_generic_ide** and this time, it booted all the way back into my installation.  "Joy!" I thought, since I had no idea why it had stopped working in the first place, I was happy to have my desktop back.

However, trouble was (and still is) afoot.  The problem is now that if I put the network under too much "stress" (i.e. listen to Pandora radio, keep a VPN up, stuff like that) the network seems to 'die'.  Once it does that, I can't connect to the internet, can't connect to the VPN, can't connect to the local Samba shares on my network, nothing.  The only solution is to reboot, and that is getting old quick.

What's going on with my computer?  Why did it work fine then not want to boot at all?  Why is my network connection dying now?

---

