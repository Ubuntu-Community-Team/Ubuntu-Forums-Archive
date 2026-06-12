---
title: "scanner &amp; WPN111 port contention?"
date: 2008-12-16
forum: General Help
---

### Post by controlUser on 2008-12-16
I've been using unbutu (my first linux experience) for about 18 months and love it.  This forum,  online posts and help pages are really useful and fun to use.  It has been satisfying to use these posts to get myself out of a few self-inflicted problems ;-)

I'm now flummoxed :confused: and need to trouble you for some help.

I am running hardy heron on an AMD K6-2 based machine and have a Mustek 1200 UB scanner.  Up until about a fortnight ago, the scanner was working fine.  Yesterday, when I came to use it (via XSane Image Scanner) the machine froze.  After switching off and rebooting, I tried the following steps:

With the scanner _not connected_

"sane-find-scanner" returned
"found USB scanner (vendor=0x1385, product=0x5f01) at libusb:001:002"

whilst "sudo sane-find-scanner" returned
found USB scanner (vendor=0x1385 [Atheros Communications Inc], product=0x5f01 [WPN111]) at libusb:001:002

With the scanner _connected_
"sane-find-scanner" returns
found USB scanner (vendor=0x055f, product=0x0006, chip=MA-1017) at libusb:002:005
found USB scanner (vendor=0x1385, product=0x5f01) at libusb:001:002

whilst "sudo sane-find-scanner" returns
found USB scanner (vendor=0x055f, product=0x0006, chip=MA-1017) at libusb:002:005
found USB scanner (vendor=0x1385 [Atheros Communications Inc], product=0x5f01 [WPN111]) at libusb:001:002

What would cause the WPN111 to be seen as a scanner?

I daren't use XSane Image Scanner nor scanimage -L because the above contention lock up the machine good and tight!  The only way out is to power down and restart :-(

I would be very grateful if someone could help me to understand what went wrong and how I should go about fixing it.

---

### Post by controlUser on 2009-01-10
Having updated to linux 2.6.24-23 the scanner now works.

I'm not suggesting a causal relationship!  I haven't really understood what caused the problem.

---

