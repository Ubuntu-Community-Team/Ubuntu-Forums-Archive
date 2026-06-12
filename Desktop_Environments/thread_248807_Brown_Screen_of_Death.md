---
title: "Brown Screen of Death"
date: 2006-09-01
forum: Desktop Environments
---

### Post by Yuffster on 2006-09-01
Alright, so last night, I figured, I'd upgrade all my stuff.  So there were like 100 upgrades.  Started that up with apt-get upgrade, or whatever, switched to another desktop and did some MUDding.

About twenty minutes in, I get the ol' SYSTEM IS GOING DOWN FOR A HALT NOW!!!!!!! message.  But it didn't shut down, it just turned into purple and blue and various other shiny colored vertical lines.  So I turned off the power and rebooted.

Log in, get a brown screen, nothing loads.

Booted in safemode, did dpkg-reconfigre --all.  Ended with stuff about Firefox not working.  Rebooted.  Brown screen of death. apt-get -f install still wants me to dpkg-reconfigure --all.

And the tricky bit--I'm on wireless and I have no idea how to make that work from the command line.

Any assistance would be greatly appreciated.

---

### Post by ceargle on 2006-09-01
Don't know about the big problem you're having, but I can help with command line wireless config.  I assume you're using DHCP.

iwconfig
# lists available wireless interfaces

iwconfig <device name> essid <ssid> key <wep key>
# sets ssid and optional wep key

dhclient <device name>
# gets ip address from DHCP server

Hope this helps!

---

