---
title: "help"
date: 2006-04-18
forum: Desktop Environments
---

### Post by runefreak on 2006-04-18
i have a compaq presario 5020 with an intagrated ad1881 sound card i need a driver where can i find one?

---

### Post by Miguel on 2006-04-18
According to the ALSA project website, your chipset is supported by either intel8x0 or via82xx drivers. These are supplied with ALSA version 1.0.10 (the version in Dapper).

Try to fiddle with settings at System-> Preferences-> Sound or System-> Preferences-> Multimedia System Selector. If the former one doesn't appear, run gstreamer-properties from the command line.

BTW: It would be nice if next time you provided more info regarding your system.

---

