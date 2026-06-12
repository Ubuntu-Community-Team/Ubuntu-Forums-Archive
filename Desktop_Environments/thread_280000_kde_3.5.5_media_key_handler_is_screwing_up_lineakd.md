---
title: "kde 3.5.5 media key handler is screwing up lineakd"
date: 2006-10-18
forum: Desktop Environments
---

### Post by enigma_0Z on 2006-10-18
I just installed kde 3.5.5, and there is (apparently) something gobbling up my mute key on my laptop. Where is the configuration for media keys in Kde 3.5.5?

---

### Post by rysiek on 2006-12-04
got the same problem today, after an upgrade to kde 3.5.5, here's how to fix it:

1. go to System Settings -> KDE Components (the rightmost option in the topmost row, might be named a bit differently, I use a translated version) -> Service Manager and unload and un-tick KMilo in the bottom window. Make sure that there's a "No" in the "Runs" column.

2. in konsole, *not* as root: killall kded; kded & (this will restart kded, without KMilo);

3. test if lineakd works - if not, restart lineakd. now it should work AOK.

if not, drop a line. ;)

HTH
rysiek

---

