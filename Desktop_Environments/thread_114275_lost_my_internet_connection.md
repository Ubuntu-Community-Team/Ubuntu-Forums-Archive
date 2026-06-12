---
title: "lost my internet connection"
date: 2006-01-08
forum: Desktop Environments
---

### Post by randomnote1 on 2006-01-08
I just installed Ubuntu a couple days ago on my laptop.  The wired connection worked fine and the wireless took a little tweaking, but it now works.  Anyway, I rebooted after working on the /etc/fstab file to see if my changes worked, and I had no internet connection.  My network works fine, I can ping my router and other computers.  I just cannot ping anything on the internet.  I can see all the information for both the eth0 and wlan0 as well as the lo.  I'm really at a loss here.

---

### Post by Ampersand on 2006-01-08
Have you tried running
```
sudo dhclient
```
from a terminal to set up your networking via dhcp (assuming your router works as a dhcp server)? Alternatively, go to System - Administration - Networking (I think) and make sure that your gateway and DNS settings are still there.

---

### Post by randomnote1 on 2006-01-09
you know, weirdest thing.  I just restarted and it just started working again.  Don't have a clue what the problem was.

---

