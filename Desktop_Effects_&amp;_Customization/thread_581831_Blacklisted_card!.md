---
title: "Blacklisted card!?"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by nw_raptor on 2007-10-19
After working around a dead cd/dvd drive, using PXE to boot and install gutsy on a friend's laptop, we decided to check the desktop effects. It's rather interesting:

Attempting to run Compiz using the 'ati' driver gave a message that the card is blacklisted. If that's the case, Feisty + Beryl/Compiz Fusion never complained about it. Overriding the checks had no effect unfortunately, so we decided to install the 'fglrx' driver and go with xserver-xgl. This seemed to work (though lagged during login), but it was until this morning that we found out that there is a serious issue with Xgl.

For some reason (it's rather random) Xgl jumps to 100% cpu usage and the system becomes totally unresponsive. Everything works (no errors etc) but it's painfully slow (even clicking has a 2-3 second lag!).

So, for now, we have decided to go back to the 'ati' driver with no Compiz.

Card is an ATI Mobility X700

I can only wish that the fglrx driver gets AIGLX support soon :(

Any ideas?

---

