---
title: "strange error (compiz/xgl maybe?)"
date: 2006-06-21
forum: Desktop Environments
---

### Post by jewishj on 2006-06-21
I am having a strange problem.  It seems that whenever the screensaver comes on (whether because I lock the computer or the computer is idle) the computer will randomly log me out.  Most of the time, I can log back in and everything is fine (so it's just a minor annoyance) but once it wouldn't load nautilus or gnome-panel and basically i had no way to do anything but ctrl+alt+backspace.

I do have compiz/XGL installed and other than this, it seems to be working flawlessly.  I am not sure that compiz is responsible for this error though because before when I was using Windows XP x64, the same thing would happen if I locked the computer overnight - it would log me out.

I looked in the system log in user.log (any other logs didn't have anything in them around the time this happened)

This is the log from last night when it happened (when nautilus didn't load either):

```

Jun 21 01:42:49 localhost gconfd (admin-9568): Resolved address "xml:readwrite:/home/admin/.gconf" to a writable configuration source at position 0
Jun 21 01:45:14 localhost hpiod: 0.9.7 accepting connections at 40268... 
Jun 21 01:45:24 localhost gconfd (admin-5327): starting (version 2.14.0), pid 5327 user 'admin'
Jun 21 01:45:24 localhost gconfd (admin-5327): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 21 01:45:24 localhost gconfd (admin-5327): Resolved address "xml:readwrite:/home/admin/.gconf" to a writable configuration source at position 1
Jun 21 01:45:24 localhost gconfd (admin-5327): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 21 01:45:24 localhost gconfd (admin-5327): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 21 01:45:24 localhost gconfd (admin-5327): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 21 01:45:26 localhost gconfd (admin-5327): Resolved address "xml:readwrite:/home/admin/.gconf" to a writable configuration source at position 0

```

When I went to bed around 3:30 or so last night, I left the screensaver on and when I got up around 12:30 I was at the login screen.  Logging back in worked fine this time, but here's the log from while I was asleep:

```

Jun 21 01:56:05 localhost gconfd (root-6303): starting (version 2.14.0), pid 6303 user 'root'
Jun 21 01:56:05 localhost gconfd (root-6303): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 21 01:56:05 localhost gconfd (root-6303): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 21 01:56:05 localhost gconfd (root-6303): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 21 01:56:05 localhost gconfd (root-6303): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 21 01:56:05 localhost gconfd (root-6303): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 21 01:57:05 localhost gconfd (root-6303): GConf server is not in use, shutting down.
Jun 21 01:57:05 localhost gconfd (root-6303): Exiting
Jun 21 03:44:53 localhost gconfd (admin-5327): Received signal 15, shutting down cleanly
Jun 21 03:44:53 localhost gconfd (admin-5327): Exiting
Jun 21 03:44:57 localhost gconfd (admin-8973): starting (version 2.14.0), pid 8973 user 'admin'
Jun 21 03:44:57 localhost gconfd (admin-8973): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 21 03:44:57 localhost gconfd (admin-8973): Resolved address "xml:readwrite:/home/admin/.gconf" to a writable configuration source at position 1
Jun 21 03:44:57 localhost gconfd (admin-8973): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 21 03:44:57 localhost gconfd (admin-8973): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 21 03:44:57 localhost gconfd (admin-8973): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 21 12:59:32 localhost gconfd (admin-8973): Resolved address "xml:readwrite:/home/admin/.gconf" to a writable configuration source at position 0

```

So it would apeear to be something to do with gconfd?

Here are my (relevant) hardware specs:
AMD 64 X2 4200+
NVidia Geforce FX 5200
SATA RAID 0 (2xWD 74GB Raptor) - root partition (using dmraid)

Thanks

---

### Post by jewishj on 2006-06-23
OK things worked great for a couple of days, and then it happened again last night:

Here is the log from lastnight

```

Jun 23 03:14:11 localhost gconfd (admin-19336): GConf server is not in use, shutting down.
Jun 23 03:14:11 localhost gconfd (admin-19336): Exiting
Jun 23 11:21:47 localhost gconfd (admin-3847): starting (version 2.14.0), pid 3847 user 'admin'
Jun 23 11:21:47 localhost gconfd (admin-3847): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 23 11:21:47 localhost gconfd (admin-3847): Resolved address "xml:readwrite:/home/admin/.gconf" to a writable configuration source at position 1
Jun 23 11:21:47 localhost gconfd (admin-3847): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 23 11:21:47 localhost gconfd (admin-3847): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 23 11:21:47 localhost gconfd (admin-3847): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 23 11:21:48 localhost gconfd (admin-3847): Resolved address "xml:readwrite:/home/admin/.gconf" to a writable configuration source at position 0
Jun 23 11:24:36 localhost gconfd (admin-3847): Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
Jun 23 11:24:36 localhost gconfd (admin-3847): None of the resolved addresses are writable; saving configuration settings will not be possible
Jun 23 11:24:36 localhost gconfd (admin-3847): Resolved address "xml:merged:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 23 11:24:36 localhost gconfd (admin-3847): None of the resolved addresses are writable; saving configuration settings will not be possible

```

I think it seems to happen whenever it tries to write to ~/.gconf at position 0.  When it tries to write at position 1 (which I see multiple times throughout the two days when everything was fine) no problems.  Anyone have any idea how to fix this?

Thanks

BTW:  It only happens when the screensaver is active/monitor is put to sleep

---

