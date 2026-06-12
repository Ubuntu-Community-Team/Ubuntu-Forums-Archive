---
title: "Dual display: RANDR missing"
date: 2009-03-28
forum: General Help
---

### Post by demothen on 2009-03-28
I'm trying to set back up my dual monitors on ubuntu 8.10, after several days of trying to get SLI working, failing, and ultimately removing the second GPU.  When I run sudo nvidia-settings I get the following:
Xlib:  extension "RANDR" missing on display ":0.0".
nvidia-settings still loads, and shows my second monitor as disabled. If I try to enable that monitor, and click apply - nothing happens.  If I exit nvidia-settings, then reload it, or click "reset" in X Server display configuration, the second monitor no longer shows up on that tab.  I have dual LG Flattron W2252TQ monitors, my primary monitor is connected to the connector closest to my motherboard via VGA with an adapter, the secondary (nonworking) monitor is connected to the second port on the same GPU with a digital cable.  I'm running a nvidia 9600gt GPU, with the 197 drivers installed, and I have tried sudo nvidia-xconfig to reset my xorg.conf file to no avail.
Any help would be appreciated.

---

### Post by Stenrad on 2009-03-28
Hi there!

Dunno if this will help you at all, but have you tried the following:-

```
gksudo nvidia-settings
```

It was the command I used when setting up my own dual display setup a few days ago. Worked a treat!

Stenrad.

---

### Post by demothen on 2009-03-28
Yeah, I did sudo instead of gksudo, but it seems to be equivilant.  No change unfortunately :(

---

### Post by Stenrad on 2009-03-28
Hi again!

Would you like me to send you a copy of my xorg config file? Maybe you could get it working that way? Let me know!

Stenrad

---

### Post by demothen on 2009-03-29
I don't know why I didn't think of that. Thanks! I actually took that idea a bit different approach, and just restored one of the backups from a couple weeks ago.  Worked perfectly after I restarted X. 
Thanks!

---

