---
title: "Easily switch between wireless/wired in KDE!"
date: 2005-06-05
forum: Desktop Environments
---

### Post by jradford on 2005-06-05
All,

I have a Thinkpad T23 configured with both Dlink-DWL-G650 and and onboard ethernet.

Switching was a pain until I ran across net-go on kde-apps.  

The net-go is a nice KDE applet, sit in your tray and does exactly what you need to switch between
profiles without dropping to a commandline.

What got me running seamlessly was this:

1. Downloaded the source
2. Added everything needed to compile it (couldnt find a package)  kde-dev's/compiled installed.
3. Add 2 profiles "home wireless" "Home Wired".  Both have "dhcp" entered, and I used dhclient in the options.

This alone allowed switching between eth0 and ath0, however in the switch the old default route was still there, so I just created 2 scripts (it gives a gui option to run an option script for each profile).

The bash scripts just do a "ifconfig eth0 down" for the wireless profile or "ifconfig ath0 down" for the wired profile, this removes the old interface out of the routing table.

The author is going to add support for this without a script in the next version.

Hope this helps someone,

-Jason

---

