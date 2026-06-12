---
title: "NetworkManager freezes Dell Studo XPS 1340"
date: 2009-02-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by djvishnu on 2009-02-18
I am experiencing some problems with my new xps, running intrepid

**Symptoms:**
 - Gnome freezes (sometimes i can move the mouse, sometimes not)
 - Corruption of graphics on parts of the screen. (sometimes kills compiz and launches metacity). Looks very much like a video card issue.
 - I can sometimes use ctrl-alt-f1 to switch to a terminal, when I switch back, the symptoms are gone. Most times i cannot do the switch, and have to do a hard reset

**This happens when:**
 - I left click on the nm-applet icon to select wlan or launch vpn.

I have switched to home made wlan connect scripts, these have not yet triggered the issue. My wlan driver is ath9k, I can try switching to the old atheros drivers if that would give any answers.


This happens quite often, but i havent been able to consistently recreate the issue.


What log files should i look at/attach to start debugging this?
What log files can be retrieved if i have to do a hard reset?

---

### Post by superm1 on 2009-02-19
8.10 or 9.04?
Which NVIDIA driver?  The 180 series has problems on 8.10, ONLY use the 177 series.

All the updates need to be installed for 8.10 for full support on this hardware.

---

### Post by djvishnu on 2009-02-19
> **superm1 said:**
> 8.10 or 9.04?
Which NVIDIA driver?  The 180 series has problems on 8.10, ONLY use the 177 series.

All the updates need to be installed for 8.10 for full support on this hardware.

Aha, I have 8.10 and 180 from proposed. Should have thought of that. I'll downgrade and report back it happens again.

Thank you.

---

### Post by venkyms on 2009-02-19
hey Thankyou for the info, will check it and if any problem, i ll downgrade to 170

regards
venkat

---

