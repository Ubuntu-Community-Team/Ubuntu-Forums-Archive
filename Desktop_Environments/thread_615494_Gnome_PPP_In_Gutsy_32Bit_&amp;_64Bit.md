---
title: "Gnome PPP In Gutsy 32Bit &amp; 64Bit"
date: 2007-11-17
forum: Desktop Environments
---

### Post by Bhawns on 2007-11-17
Gnome PPP Works well dialing and connecting in both 32bit & 64bit Gutsy. I have a Hayes Accura External Modem. The problem is that after the dialup and connection process takes place Gnome PPP does not say "connected" and minimize and dock in the notification area as is the case in Fiesta 7.04. In 7.04 it works perfectly.
I have ddone all that needs to be done to make this happen. I run fiesta 7.04 64bit and it works perfectly as an OS.
Will any of the updates for Gutsy solve this problem?
Canon PIXMA ip1800 I also need some help with this, driver location or advice.

Thanks, Ubuntu is great! 
I am booting Gutsy 64bit, Fiesta 64 bit Windows XP Pro and it seems any OS I want also  I can read and write to any OS thanks to Gutsy. I love it!

---

### Post by mdebusk on 2007-11-17
> **Bhawns said:**
> Gnome PPP Works well dialing and connecting in both 32bit & 64bit Gutsy. I have a Hayes Accura External Modem. The problem is that after the dialup and connection process takes place Gnome PPP does not say "connected" and minimize and dock in the notification area as is the case in Fiesta 7.04. In 7.04 it works perfectly.

It's a known bug. Something about WVDial was changed and GnomePPP doesn't understand its new output. I've switched to [PPPTray](http://gnomefiles.org/app.php/PPP+Tray+Icon) and am satisfied with it. Just run pppconfig from the command line, answer the questions, and install the package, and you should be set.

---

### Post by Bhawns on 2007-11-17
I really do think they should deal with this sooner than later because this is the easiest way to connect and disconnect also it`s fast and efficient in fiesta.
So developers stay working and what about the resistance to canon printers e.g PIXMA ip1800?

---

