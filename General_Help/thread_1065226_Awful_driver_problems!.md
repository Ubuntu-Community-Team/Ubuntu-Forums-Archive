---
title: "Awful driver problems!"
date: 2009-02-09
forum: General Help
---

### Post by photon_man62 on 2009-02-09
(Sorry if this is miscategorized, I didn't know where to put this)
-
Hello. I am having awful display problems at the moment. This is what I did to get here:

I wanted to install the newest nVIDIA drivers (180.11). So I downloaded the .run, went into the virtual terminal (ctrl+alt+f1), exited the X Server and tried to run the .run file with the driver.  I installed the driver, and it asked if I want to look on the net for some kernel stuff, so I said yes, then it said it couldn't find anything and made its own display kernel. Well, in the end it installed and I rebooted.

I tried to boot, but I noticed that in the boot screen there was

```
 nvidia (107.something)...
```

And I installed 108.11, so I thought this was weird. Anyways, it booted me into a really messed up "Low Graphics Mode". I reconfigured the system to a new configuration (I installed a new driver, so... yeah) and it restarted the display. Well, same thing happened, so I reconfigured it to the default configuration. I rebooted and... THE SAME THING. So I booted into Low Graphics Mode and reinstalled nvidia-common, then disabled the "nvidia" driver in Hardware Drivers. I rebooted again, but now the Low Graphics Mode was properly sized, so I reloaded the default configuration. Rebooted. Now I got a proper GUI :D

So I tried installing the newest driver (180.11) again. I got the low graphics again, so I reloaded the default config and now tried installing the 177 proprietary driver. Now I get a messed up Low Graphics Mode... AGAIN.
-
I can also say that ALL the time,

```
 nvidia (107.something)...
```

was (and still is) on the boot screen (text that appears while booting). And that the boot screen stays for like 30 seconds at

```
... Mail Transport Agent [MTA] sendmail 
```
---
Any help, guys?

Like how to remove the 180.11 driver, or the 177 driver?

---

### Post by photon_man62 on 2009-02-09
Sorry but I have to bump this up. :(

Any ideas?

---

### Post by photon_man62 on 2009-02-09
Bumping up again, sorry, but this is URGENT.

---

