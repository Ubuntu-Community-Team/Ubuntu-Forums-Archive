---
title: "GNOME Randomly Initiates Shut-down"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Yuffster on 2006-07-07
Yeah, I just installed Ubuntu, love it to death.

One minor problem, though.  It's randomly shut itself down about 10 times since last night.  Somewhat annoying.

I checked the /var/log and it shows up this around the shutdowns (just a random selection, and I don't really know what's relevant):

> 
Jul  6 22:56:26 neo-hadsell kernel: [4296408.892000] drivers/usb/net/atmel/at76c503.c: registered wlan0
Jul  6 22:58:24 neo-hadsell gconfd (root-5648): GConf server is not in use, shutting down.
Jul  6 22:58:24 neo-hadsell gconfd (root-5648): Exiting
Jul  6 22:58:33 neo-hadsell shutdown[9207]: shutting down for system halt
Jul  6 22:58:35 neo-hadsell gconfd (m-5059): Received signal 15, shutting down cleanly
...
Jul  7 02:41:27 localhost gconfd (root-5968): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul  7 02:41:27 localhost gconfd (root-5968): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul  7 02:41:27 localhost gconfd (root-5968): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul  7 02:41:27 localhost gconfd (root-5968): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul  7 02:41:27 localhost gconfd (root-5968): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul  7 02:41:57 localhost gconfd (root-5968): GConf server is not in use, shutting down.
Jul  7 02:41:57 localhost gconfd (root-5968): Exiting
Jul  7 02:42:43 localhost shutdown[6521]: shutting down for system halt
Jul  7 02:42:45 localhost gconfd (m-4881): Recei
...
Jul  7 11:06:40 localhost gconfd (root-8017): SIGHUP received, reloading all databases
Jul  7 11:06:40 localhost gconfd (root-8017): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jul  7 11:06:40 localhost gconfd (root-8017): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jul  7 11:06:40 localhost gconfd (root-8017): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jul  7 11:06:40 localhost gconfd (root-8017): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jul  7 11:06:40 localhost gconfd (root-8017): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jul  7 11:06:40 localhost gconfd (root-8017): GConf server is not in use, shutting down.
Jul  7 11:06:40 localhost gconfd (root-8017): Exiting
Jul  7 11:19:31 localhost -- MARK --
Jul  7 11:20:58 localhost shutdown[8801]: shutting down for system halt
Jul  7 11:21:00 localhost gconfd (m-4952): Received signal 15, shutting down cleanly
Jul  7 11:21:01 localhost gconfd (m-4952): Exiting
...
Jul  6 22:56:26 neo-hadsell kernel: [4296408.891000] drivers/usb/net/atmel/at76c503.c: firmware version 1.101.0 #86 (fcs_len 4)
Jul  6 22:56:26 neo-hadsell kernel: [4296408.891000] drivers/usb/net/atmel/at76c503.c: device's MAC 00:0c:41:5c:e4:0a, regulatory domain FCC (U.S) (id 16)
Jul  6 22:56:26 neo-hadsell kernel: [4296408.892000] drivers/usb/net/atmel/at76c503.c: registered wlan0
Jul  6 22:58:24 neo-hadsell gconfd (root-5648): GConf server is not in use, shutting down.
Jul  6 22:58:24 neo-hadsell gconfd (root-5648): Exiting
Jul  6 22:58:33 neo-hadsell shutdown[9207]: shutting down for system halt


Any ideas?

---

