---
title: "PPPOE stopped working"
date: 2005-10-14
forum: Desktop Environments
---

### Post by chiok on 2005-10-14
Howdy.  To get networking up in Hoary, I had to run pppoeconf once and then comment out make_resolv_conf() in /etc/dhcp3/dhclient-script to stop it from disconnecting after five minutes.  It was fine after that initial setup.

I upgraded to Breezy a week before it was official and networking continued to work.  In the last 24h, it stopped working.  I can run pppoeconf to get it working again, but I have to do it after every reboot.  Apache2 and Samba are, of course, still down.

I did a fresh install, but I still have to run pppoeconf after every reboot.

Any ideas?

---

### Post by chiok on 2005-10-14
Oh sorry.  This is the wrong forum.  Can I delete this?

---

