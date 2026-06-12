---
title: "Automatically restarting / forgetting settings?"
date: 2009-04-22
forum: General Help
---

### Post by weirdbeardmt on 2009-04-22
When I booted the machine yesterday, for some reason the network settings on eth1 had been reset from a manual IP back to DHCP. I put everything back and it was all working fine when I went to bed.

When I got up this morning, it seems like the machine has been restarted (because the terminal windows that were open when I left it, aren't there anymore) and for some reason the network setting has gone back to DHCP again... 


In the syslog, there's this line around 623am this morning.

syslogd 1.5.0#2ubuntu6: restart

Any ideas what's causing the restart and why my eth settings are getting lost?

---

### Post by cariboo on 2009-04-22
The problem you are having is a know problem with network manager. The way I have gotten around it is to uninstall network-manager-gnome and installed network-manager-admin. As for youe computer restarting over night, it could have been from a power bump.

The message your got is just the syslog daemon restarting, which it does every 24 hours.

---

### Post by weirdbeardmt on 2009-04-22
Hi cari - thanks. I'll investigate the network-manager part.

Not sure the restart was caused by a power bump - when I was playing this morning, it did it again. 

It could well be a hardware thing unrelated to Ubuntu, but it had otherwise been sat there for a week quite happily with no issues. I did install a bunch of updates tho, so I wonder if that's part of the problem.

---

