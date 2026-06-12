---
title: "K(Ubuntu) freezes when idle for several hours"
date: 2005-12-19
forum: Desktop Environments
---

### Post by drange on 2005-12-19
Hello.

I'm using Kubuntu 5.10 (upgraded from Ubuntu 5.04) and I have a problem. When I go to sleep with my computer turned on (and logged in to KDE), the screen wont turn back on again. I move the mouse and press keys on the keyboard.

I have tried CTRL-ALT-BACKSPACE, CTRL-ALT-1&#8594;6 and so on, but nothing seems to help. Even tried the good old CTRL-ALT-DELETE.

So I have to manually hard reboot it.

From my messages:

```
Dec 16 16:10:58 localhost kernel: [4294732.407000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Dec 16 16:10:58 localhost kernel: [4294732.407000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
Dec 16 16:10:58 localhost kernel: [4294732.407000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
Dec 16 16:10:58 localhost kernel: [4294732.412000] [drm] Loading R200 Microcode
Dec 16 16:14:45 localhost ivman: Ivman started in system mode
Dec 16 16:18:08 localhost gconfd (drange-7930): starting (version 2.12.0), pid 7930 user 'drange'
Dec 16 16:18:08 localhost gconfd (drange-7932): starting (version 2.12.0), pid 7932 user 'drange'
Dec 16 16:18:08 localhost gconfd (drange-7932): Failed to get lock for daemon, exiting: Failed to lock '/tmp/gconfd-drange/lock/ior': probably another process has the lock,
or your operating system has NFS file locking misconfigured (Resource temporarily unavailable)
Dec 16 16:18:09 localhost gconfd (drange-7930): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Dec 16 16:18:09 localhost gconfd (drange-7930): Resolved address "xml:readonly:/usr/share/gconf/local.mandatory" to a read-only configuration source at position 1
Dec 16 16:18:09 localhost gconfd (drange-7930): Resolved address "xml:readwrite:/home/drange/.gconf" to a writable configuration source at position 2
Dec 16 16:18:09 localhost gconfd (drange-7930): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Dec 16 16:18:09 localhost gconfd (drange-7930): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Dec 16 16:18:09 localhost gconfd (drange-7930): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Dec 16 16:18:09 localhost gconfd (drange-7930): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Dec 16 16:18:09 localhost gconfd (drange-7930): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Dec 16 16:19:07 localhost exiting on signal 15
Dec 16 16:19:09 localhost syslogd 1.4.1#17ubuntu3: restart.
Dec 16 16:39:09 localhost -- MARK --
Dec 16 16:59:09 localhost -- MARK --
Dec 16 17:19:10 localhost -- MARK --
Dec 16 17:31:09 localhost gconfd (drange-7930): GConf server is not in use, shutting down.
Dec 16 17:31:09 localhost gconfd (drange-7930): Exiting
Dec 16 17:59:10 localhost -- MARK --
Dec 16 18:19:10 localhost -- MARK --
Dec 16 18:39:10 localhost -- MARK --
Dec 16 18:59:10 localhost -- MARK --
Dec 16 19:19:10 localhost -- MARK --
Dec 16 19:39:10 localhost -- MARK --
Dec 16 19:59:10 localhost -- MARK --
Dec 16 20:19:10 localhost -- MARK --
Dec 16 20:39:10 localhost -- MARK --
Dec 16 20:59:10 localhost -- MARK --
Dec 16 21:19:11 localhost -- MARK --
Dec 16 21:39:11 localhost -- MARK --
Dec 16 21:40:38 localhost syslogd 1.4.1#17ubuntu3: restart.
Dec 16 21:40:38 localhost kernel: Inspecting /boot/System.map-2.6.12-10-386
Dec 16 21:40:39 localhost kernel: Loaded 29010 symbols from /boot/System.map-2.6.12-10-386.
Dec 16 21:40:39 localhost kernel: Symbols match kernel version 2.6.12.
```

I guess I fell asleep about 17:00 and had to cut the power aproximately 21:40

I did, however, NOT reboot 16:19, so why the syslogd did, I have no clue.

Any good advices? According to syslogd, nothing is happening to the point where I reboot.

---

### Post by drange on 2005-12-20
If anybody knows **anything**! Please tell me.

---

### Post by Mortal on 2005-12-21
I know that this has also happened to mee on my laptop. I thought it might have something to do with the ati-drivers, but haven't investigated any further. I installed Ubuntu 5.10 and then installed kubuntu-desktop.

---

### Post by HermanAB on 2005-12-21
Sure it only happens when idle?

I have found machines lock up while using them - just stops dead in its tracks.  The reason was xorg.  Upgraded that and the problem went away.

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by drange on 2005-12-22
Yes, it only happens when I'm not using my computer for several hours. Happened again yesterday. And it doesn't seem to happen on my girlfriends user account.

---

### Post by HermanAB on 2005-12-22
Bad screen saver or power settings?

---

### Post by drange on 2005-12-31
HermanAB: Not impossible... I have disabled all power settings and screen savers and it hasn't happened to me since. But I have to try it a bit more to be convinced.

I will let it be logged in over the weekend and then will we see.

---

### Post by drange on 2006-01-09
For the record, my computer hasn't frozen after I removed all power and screen saver settings.

---

