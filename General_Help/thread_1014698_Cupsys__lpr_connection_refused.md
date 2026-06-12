---
title: "Cupsys : lpr connection refused"
date: 2008-12-18
forum: General Help
---

### Post by Black7n on 2008-12-18
I got a client computer that have Ubuntu 8.04 and running latest cupsys on it.

I can set up printers and print test pages, but when trying to print from lets say FireFox as an example the printers wont show.

In printer configuration (System -> Administration -> printing) the goto server field is filled in with "printserver.network.net" insted of localhost.

Iw also found two .cupsrc (and .cupsrc~) files in the users home folder that contains the "printserver.network.net" address.

Error messages is :
"Lpr connection refused" when trying to print to any of the printers iw set up.

The /var/log/cups/error_log dont say anyting atm

Iw tried removing cupsys + everything that has to do with cupsys and then reinstalling it but i still have the same problem.

Using another user on the machine works tho so i guess its a user configuration problem or just old leftovers seens upgrading to 8.04.

Anyone got any clue on what i should edit or remove to make this work :confused:

---

### Post by jnorthr on 2008-12-18
perhaps you may gain further clues by looking at /var/log/syslog

system>administration>system log

then click on syslog in left column. do you see any cups related messages for either you or your co-worker that relate to cups ?

---

### Post by Black7n on 2008-12-18
```
Dec 17 12:31:20 avc1 cupsd[25365]: *** WARNING *** The program 'cupsd' uses the Apple Bonjour compatibility layer of Avahi.
Dec 17 12:31:20 avc1 kernel: [3099817.567937] audit(1229513480.866:48): type=1503 operation="inode_permission" requested_mask="::r" denied_mask="::r" name="/home/user1/.cupsrc" pid=25365 profile="/usr/sbin/cupsd" namespace="default"
Dec 17 12:31:20 avc1 cupsd[25365]: *** WARNING *** Please fix your application to use the native API of Avahi!
Dec 17 12:31:20 avc1 cupsd[25365]: *** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd>
Dec 17 12:54:03 avc1 -- MARK --
Dec 17 13:14:03 avc1 -- MARK --
Dec 17 13:14:41 avc1 cupsd[26001]: *** WARNING *** The program 'cupsd' uses the Apple Bonjour compatibility layer of Avahi.
Dec 17 13:14:41 avc1 cupsd[26001]: *** WARNING *** Please fix your application to use the native API of Avahi!
Dec 17 13:14:41 avc1 cupsd[26001]: *** WARNING *** For more information see <http://0pointer.de/avahi-compat?s=libdns_sd&e=cupsd>

```

Found this in the syslog. Looking into Avahi as we speak.

---

### Post by Black7n on 2008-12-18
Solved

removing the .cupsrc solved the problem.

---

