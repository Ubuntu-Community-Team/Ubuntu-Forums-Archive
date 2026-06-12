---
title: "Regular Freezes / Reboots (Gconfd/X?)"
date: 2006-08-16
forum: Desktop Environments
---

### Post by bjc on 2006-08-16
I've been using Dapper for at least four months but in the last week I've started seeing freezes. X locks up, the bottom half of the screen displays garbled video, then X restarts. I'm using the Nvidia drivers, but, as I say, they've been working fine up to this point.

The X log doesn't show anything useful, and syslog just has:
```

Aug 17 04:19:58 localhost gconfd (ben-32544): Received signal 15, shutting down cleanly
Aug 17 04:19:58 localhost gconfd (ben-32544): Exiting
Aug 17 04:19:59 localhost gconfd (ben-23720): starting (version 2.14.0), pid 23720 user 'ben'
Aug 17 04:19:59 localhost gconfd (ben-23720): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug 17 04:20:00 localhost gconfd (ben-23720): Resolved address "xml:readwrite:/home/ben/.gconf" to a writable configuration source at position 1
Aug 17 04:20:00 localhost gconfd (ben-23720): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2Aug 17 04:20:00 localhost gconfd (ben-23720): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug 17 04:20:00 localhost gconfd (ben-23720): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug 17 04:20:03 localhost /USR/SBIN/CRON[23728]: (debarchiver) CMD (test -x /usr/bin/debarchiver && /usr/bin/debarchiver -so | logger -t debarchiver -p daemon.info)
Aug 17 04:20:06 localhost gdm[32477]: Error reinitilizing server

```

Apart from checking RAM, where should I start debugging this?

---

### Post by bjc on 2006-08-17
Any ideas before I have to reinstall?

---

