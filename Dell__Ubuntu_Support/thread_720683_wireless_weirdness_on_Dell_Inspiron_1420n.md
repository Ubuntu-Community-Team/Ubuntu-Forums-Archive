---
title: "wireless weirdness on Dell Inspiron 1420n"
date: 2008-03-10
forum: Dell  Ubuntu Support
---

### Post by speedeep on 2008-03-10
I've got a Dell Inspiron 1420n running Gutsy Gibbon (from Dell) with all current patches/updates.
Linksys WRT54G running Tomato 1.15 firmware.
(the Linksys is working fine with several other Ubuntu (also Gutsy, Fedora, and CentOS computers without these issues.)

Periodically my wireless network connection disappears and what usually shows up usually as the "Wireless" connection in the "Manual Configure" network configuration util "turns into" a "Wired" connection (showing dhcp options instead of ssid options as expected.)  When this happens, I have two Wired connections (eth0 and eth1) but I'm not connected via Ethernet, so that doesn't do me any good.

before/after screenshots are attached:  
netprobbefore.png is my normal operating settings for wireless only.
netprobafter.png is after I lose my connections and go look at the settings
This happens with no action on my part and sometime when I'm not even around.

There doesn't seem to be a pattern as to how long (sometimes 5 minutes on laptop, sometimes 24 hours) I've been using the laptop, what I'm doing on the laptop, or even if I'm using the laptop at all (sometimes I'll come back to the laptop after a day or so and find the networking all jumbled up.)

I've seen some references to "sudo /etc/init.d/networking restart" then "dhclient ifname" around, but that doesn't seem to correct me problem.  I unfortunately usually end up rebooting.

All my other Linux boxen behave how I tell them to.  I hate to see these "weird behaviors" on a Dell-provided hardware/OS combo.  Is anyone else having this problem?

---

### Post by fragos on 2008-03-10
My 1420n will occasionaly loose a Wifi connection with a linksys AP that at best offers a low signal strength and is busy.  It has however never called eth1 a 2nd wired port.  With my home AP I never loose the signal.  I suggest you look in [http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10) for solutions to Dell Ubuntu problems.  You might try using the iwl driver they recommend.

---

