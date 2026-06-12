---
title: "Ubuntu hangs when booting"
date: 2009-05-15
forum: General Help
---

### Post by krazykookmany on 2009-05-15
//

---

### Post by malaprohibita on 2009-05-15
I don't have a solution, I'm afraid, but I can attest that I've been getting the same error, down to the frozen, fuzzy screen.  I tried a complete reinstallation (dual-booting with vista on core i7 dell studio xps 435mt), but for some reason it's failing entirely.  That's another issue for another forum, but what you're experiencing is how my troubles began.

---

### Post by krazykookmany on 2009-05-15
//

---

### Post by malaprohibita on 2009-05-15
Yeah, every method of installation I've tried (64bit) has completely choked.  For the moment I'm stumped.  I'm pretty sure it was the x.org server that went bonkers first, since my xorg.conf file was void of any device-specific settings.  This was even after re-running the xorg configuration.  The last thing I tried before nuking the install was a PPA from launchpad:
[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill]("https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill").  It worked for some users, but not others.  It might be worth checking out.  I know I'm not going to give up.:D

---

