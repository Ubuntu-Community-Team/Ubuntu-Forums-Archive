---
title: "System no longer boots. Hangs @ Network Configuration"
date: 2008-01-04
forum: Desktop Environments
---

### Post by Erik Visser on 2008-01-04
Greetings,

Am having some challenges with booting my desktop (darn thing won't boot anymore)

Problem started after my computer locked up using the network manager. Tried to boot using the 'reset' button as well as removing power from the computer.

When booting Ubuntu 7.10, kernel 2.6.22-14-generic, the HDD LED flashes for some time and then it just hangs.
When booting Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode), all goes well until it comes to section where it configures the network interfaces. At this stage, I see a blinking cursor and that's it......(it blinks and blinks...and blinks).

Details
Computer: Fujitsu Siemens computer with AMD Athlon XP 3000+ processor
Ubuntu 7.10 built on 20071016
PCI Ethernet Card by VIA Technologies, Device VT6102 [Rhine-II]
PCI WLAN Card by Netgear (WG311T)

I had everything pretty much up and running (incl WLAN) with the right driver and such. WLAN card was able to 'see' wireless networks and I was about to get it to connect to my WLAN router. At this stage, I changed the WLAN configuration in the network manager after which my computer completely froze. Since then I've been unable to boot from my HDD (it does boot from the CD). Even booting in 'safe mode' does not work.

Would appreciate if someone could give me some guidance on how to proceed (at this stage I see re-installing Ubuntu as my last resort).

Cheers,

Erik

Note: Needless to say that I am a newcomer in the realms of Ubuntu/Linux

---

### Post by metalheart on 2008-01-04
Remove wireless card, try to boot. Shut down, reinsert wireless card and try to boot again. Maybe this will let you create new network configuration.

---

### Post by Erik Visser on 2008-01-05
Thanks very much for the info.

Rather than opening up my PC to remove the PCI WLAN card, (try to) reboot, re-insert the PCI card and boot again I did the following;

[LIST]
[*]Re-install Ubuntu
[*]Used command line entries (found at other forum postings for the WG311 card) to get everything going
[/LIST].
Just one hint to folks posting these tips at the forums............PLEASE indicate when one has to reboot the computer....Did everything per the instructions and things simply didn't work....until I rebooted.

Once again, thanks for the effort of providing some guidance though.

Cheers,

A novice.

---

### Post by SimonFinch on 2008-01-07
This is the same as what happened to me ([See this post]("http://ubuntuforums.org/showthread.php?t=660778")) It haven't  tried the re-install yet though.  I've uninstalled network manager and rebooted several times but although I've now got my wired NW working ok, every time I try to go into Network Manager everything goes very slowly and hangs.

---

