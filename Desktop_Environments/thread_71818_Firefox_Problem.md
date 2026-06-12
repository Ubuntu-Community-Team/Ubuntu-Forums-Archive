---
title: "Firefox Problem"
date: 2005-10-04
forum: Desktop Environments
---

### Post by groundpounder on 2005-10-04
I'm running Hoary on an old 533MHz K6-2.  The other day, Firefox crashed.  I haven't been able to restart it since, even after rebooting the computer.  I get the button that says "Starting Firefox for a few seconds, then nothing.  I have tried removing it and reinstalling with Synaptic with no luck.

---

### Post by localzuk on 2005-10-04
This sounds like it could be a few different things.

1. Some of the options in your personal settings for firefox could be corrupt - delete the .mozilla/firefox directory
2. Some settings are being kept when removing firefox, try "apt-get --purge remove firefox" to try and remedy this.

Hope this helps

---

### Post by shakin on 2005-10-04
I'd start by making sure there is no firefox-bin process running. If your session gets saved whenever you logout you may have inadvertently saved a crashed firefox process.

run: 'killall firefox-bin' from the command line, then try running firefox again.

---

### Post by groundpounder on 2005-10-04
I tried 'killall firefox-bin' first, and that worked.  Thanks a lot!  Gotta love this forum!  :)

---

