---
title: "Zire 31 and gPilot"
date: 2006-02-03
forum: Desktop Environments
---

### Post by trekkie1701c on 2006-02-03
I installed Ubuntu on my computer recently; everything works except for gPilot.  After going through several threads about my issue and googling it, I still have had no luck in finding a resolution.

Here's what's going on:

When I start up the setup for gPilot, the default device is /dev/pilot - which appears when  my Zire isn't connected (which I've been able to find out isn't supposed to happen). Aside from that, only three other devices are listed, none of which will allow me to sync my PDA (I'll post an edit later with the devices - can't access the internet from my computer until I get a network card for it).

When I get to the initial sync screen, and tap the hotsync button on my PDA, nothing happens (aside from my PDA's eventual error message "Could not connect to the desktop").

---

### Post by wbmj on 2006-02-04
When you first use the gPilot setup, did you set the connection as a USB?

---

### Post by trekkie1701c on 2006-02-11
No.  The four options were for what appeared to be three serial ports and the pilot, none of which worked.  I tried to create a reference to my USB ports using instructions I found on the forums in another topic (did some searching before I posted this) and got invalid device messages - and yes, I tried creating it while running as root.

---

### Post by rlaska on 2006-11-13
trekkie: I don't know if you're still struggling with this, but for documentation purposes, the way I got it to work was to use /dev/ttyUSB1 instead of /dev/pilot. I just did an "ls -l /dev/pilot" to see what it was symlinked to, and use that device file instead. It's not perfect, but it works most of the time.

---

