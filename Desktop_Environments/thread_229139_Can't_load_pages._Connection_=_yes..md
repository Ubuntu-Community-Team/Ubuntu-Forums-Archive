---
title: "Can't load pages. Connection = yes."
date: 2006-08-04
forum: Desktop Environments
---

### Post by PseudoEvolution on 2006-08-04
So I installed Dapper to dual boot with XP pro. The network was detected, as normal, for both OS's. I can connect and browse sites on Windoze, but I can't browse sites on Ubuntu.
I can ping, trace, open ftp/ssh sessions and even download the updates for Ubuntu (sometimes it fails), but when I open any browser, I can't load any websites. My network settings are all correct and my router is configured. Hardware wise, everything is fine. 
So any ideas why my browsers wont browse? ='O
(No firewalls installed either)

---

### Post by OpsVentus on 2006-08-04
Can you give more information on your connection? Do you use a proxy? Which browser, firefox?
Which connection settings are in firefox?

Cheers,
Bart.

---

### Post by PseudoEvolution on 2006-08-04
Well I can't check exact settings without booting ubuntu and writing them down on paper. 
But, I can tell you that I don't use a proxy, and the _firefox_ settings are set to direct connect. 

Using DSL (my modem acts as a gateway). My IP is DHCP, so my network settings for eth0 is set for DHCP as it should.

If you want me to get some specific information, I can boot up and write it down. Since I can't browse on it, I would like to know what I'm looking for. :P

---

### Post by OpsVentus on 2006-08-04
Maybe this:
[http://www.ubuntuforums.org/showthread.php?t=222047](http://www.ubuntuforums.org/showthread.php?t=222047)
Or this:
[http://www.ubuntuforums.org/showthread.php?t=87798](http://www.ubuntuforums.org/showthread.php?t=87798)

Cheers,
Bart.

---

### Post by PseudoEvolution on 2006-08-04
Thanks! I think that first one might work... brb




[edit]
Woot! network.dns.disableIPv6 to 'true' = success!
Thanks!



Oh yeah, that reminds me... Is there a way to _not_ mount a drive when I boot? I like a clean desktop for linux, and having to 'umount' my windows hda1 everytime I boot is annoying. :F
I don't need it, and if I ever do, I can mount it myself.

---

### Post by OpsVentus on 2006-08-04
Commentout the line in your fstab.
sudo gedit /etc/fstab
Put an # infront of the line starting with '/dev/hda1'.

Bart.

---

