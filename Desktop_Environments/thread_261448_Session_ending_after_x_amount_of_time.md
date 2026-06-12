---
title: "Session ending after x amount of time"
date: 2006-09-20
forum: Desktop Environments
---

### Post by hotstovejer on 2006-09-20
Hey all, running DD with Compiz, and all was well until yesterday, when all of a sudden, when my screensaver is supposed to start, it logs me out of the session, and I end up back at my login screen. I checked out the syslog, and here is what I think is happening. Just don't know how to fix it.


```
Sep 20 07:37:19 cutiepie syslogd 1.4.1#17ubuntu7: restart.
Sep 20 07:37:19 cutiepie anacron[841]: Job `cron.daily' terminated
Sep 20 07:37:19 cutiepie anacron[841]: Normal exit (1 job run)
Sep 20 07:43:07 cutiepie dhclient: DHCPREQUEST on eth0 to 24.116.2.172 port 67
Sep 20 07:43:07 cutiepie dhclient: DHCPACK from 24.116.2.172
Sep 20 07:43:07 cutiepie dhclient: bound to 24.119.109.178 -- renewal in 38729 seconds.
Sep 20 07:57:19 cutiepie -- MARK --
Sep 20 08:06:04 cutiepie gconfd (hotstovejer-1102): starting (version 2.14.0), pid 1102 user 'hotstovejer'
Sep 20 08:06:04 cutiepie gconfd (hotstovejer-1102): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep 20 08:06:04 cutiepie gconfd (hotstovejer-1102): Resolved address "xml:readwrite:/home/hotstovejer/.gconf" to a writable configuration source at position 1
Sep 20 08:06:04 cutiepie gconfd (hotstovejer-1102): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep 20 08:06:04 cutiepie gconfd (hotstovejer-1102): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep 20 08:06:04 cutiepie gconfd (hotstovejer-1102): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep 20 08:06:06 cutiepie gconfd (hotstovejer-1102): Resolved address "xml:readwrite:/home/hotstovejer/.gconf" to a writable configuration source at position 0
Sep 20 08:17:01 cutiepie /USR/SBIN/CRON[1552]: (root) CMD (   run-parts --report /etc/cron.hourly)
Sep 20 08:28:06 cutiepie kernel: [17298520.228000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 08:28:15 cutiepie kernel: [17298529.228000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 08:28:15 cutiepie kernel: [17298529.228000] NVRM: Xid (0001:00): 28,  L1 -> L0
Sep 20 08:28:24 cutiepie kernel: [17298538.232000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 08:28:24 cutiepie kernel: [17298538.232000] NVRM: Xid (0001:00): 28,  L1 -> L0
Sep 20 08:28:33 cutiepie kernel: [17298547.236000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 08:28:33 cutiepie kernel: [17298547.236000] NVRM: Xid (0001:00): 28,  L1 -> L0
Sep 20 08:28:42 cutiepie kernel: [17298556.240000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 08:28:42 cutiepie kernel: [17298556.240000] NVRM: Xid (0001:00): 28,  L1 -> L0
Sep 20 08:28:51 cutiepie kernel: [17298565.244000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 08:28:51 cutiepie kernel: [17298565.244000] NVRM: Xid (0001:00): 28,  L1 -> L0
Sep 20 08:29:00 cutiepie kernel: [17298574.248000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 08:29:00 cutiepie kernel: [17298574.248000] NVRM: Xid (0001:00): 28,  L1 -> L0
Sep 20 08:29:09 cutiepie kernel: [17298583.252000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 08:29:09 cutiepie kernel: [17298583.252000] NVRM: Xid (0001:00): 28,  L1 -> L0
Sep 20 08:29:18 cutiepie kernel: [17298592.256000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 08:43:37 cutiepie gdm[771]: Error reinitilizing server
Sep 20 08:43:38 cutiepie kernel: [17299453.732000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Sep 20 08:43:38 cutiepie kernel: [17299453.732000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Sep 20 08:43:38 cutiepie kernel: [17299453.736000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Sep 20 08:43:39 cutiepie gconfd (hotstovejer-1102): GConf server is not in use, shutting down.
Sep 20 08:43:39 cutiepie gconfd (hotstovejer-1102): Exiting
Sep 20 08:48:10 cutiepie gconfd (hotstovejer-2203): starting (version 2.14.0), pid 2203 user 'hotstovejer'
Sep 20 08:48:10 cutiepie gconfd (hotstovejer-2203): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep 20 08:48:10 cutiepie gconfd (hotstovejer-2203): Resolved address "xml:readwrite:/home/hotstovejer/.gconf" to a writable configuration source at position 1
Sep 20 08:48:10 cutiepie gconfd (hotstovejer-2203): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep 20 08:48:10 cutiepie gconfd (hotstovejer-2203): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep 20 08:48:10 cutiepie gconfd (hotstovejer-2203): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep 20 08:48:13 cutiepie gconfd (hotstovejer-2203): Resolved address "xml:readwrite:/home/hotstovejer/.gconf" to a writable configuration source at position 0
Sep 20 09:01:30 cutiepie kernel: [17300524.076000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 09:01:39 cutiepie kernel: [17300533.080000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 09:01:39 cutiepie kernel: [17300533.080000] NVRM: Xid (0001:00): 28,  L1 -> L0
Sep 20 09:01:48 cutiepie kernel: [17300542.084000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 09:01:48 cutiepie kernel: [17300542.084000] NVRM: Xid (0001:00): 28,  L1 -> L0
Sep 20 09:01:57 cutiepie kernel: [17300551.088000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 09:01:57 cutiepie kernel: [17300551.088000] NVRM: Xid (0001:00): 28,  L1 -> L0
Sep 20 09:02:06 cutiepie kernel: [17300560.092000] NVRM: Xid (0001:00): 8, Channel 00000002
Sep 20 09:02:06 cutiepie kernel: [17300560.092000] NVRM: Xid (0001:00): 28,  L1 -> L0
Sep 20 09:05:44 cutiepie gconfd (hotstovejer-2203): Resolved address "xml:merged:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 0
Sep 20 09:05:44 cutiepie gconfd (hotstovejer-2203): None of the resolved addresses are writable; saving configuration settings will not be possible
Sep 20 09:05:44 cutiepie gconfd (hotstovejer-2203): Resolved address "xml:merged:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep 20 09:05:44 cutiepie gconfd (hotstovejer-2203): None of the resolved addresses are writable; saving configuration settings will not be possible
```

So any idea why all of a sudden, I would just be logged out?

Thanks for all the help!

Jeremy

---

### Post by mushr00m on 2006-10-04
I'm having the exact same problem. Dapper with xgl/beryl in my case.  I started the computer this morning to turn on the radio(streaming with VLC) and within 30 seconds the computer had logged me out of the seesion, back to the login screen.

The only programs I was running:
VLC
aMSN

compiz/beryl wasn't running at the time because I use metacity with XGL at startup.

any clues?


```
Oct  4 07:03:48 localhost syslogd 1.4.1#17ubuntu7: restart.
Oct  4 07:03:48 localhost anacron[5100]: Job `cron.daily' terminated
Oct  4 07:03:48 localhost anacron[5100]: Normal exit (1 job run)
Oct  4 07:08:30 localhost gconfd (xxxxxxxxx-5945): Received signal 15, shutting down cleanly
Oct  4 07:08:30 localhost gconfd (xxxxxxxxx-5945): Exiting
Oct  4 07:08:31 localhost gdm[5877]: Error reinitilizing server
Oct  4 07:08:32 localhost kernel: [17180344.072000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Oct  4 07:08:32 localhost kernel: [17180344.072000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Oct  4 07:08:32 localhost kernel: [17180344.072000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Oct  4 07:17:01 localhost /USR/SBIN/CRON[6315]: (root) CMD (   run-parts --report /etc/cron.hourly)
Oct  4 07:30:01 localhost /USR/SBIN/CRON[6317]: (root) CMD (test -x /etc/init.d/anacron && /usr/sbin/invoke-rc.d anacron start >/dev/null)
Oct  4 07:30:01 localhost anacron[6339]: Anacron 2.3 started on 2006-10-04
Oct  4 07:30:01 localhost anacron[6339]: Normal exit (0 jobs run)
Oct  4 07:30:17 localhost gconfd (xxxxxxxxx-6392): starting (version 2.14.0), pid 6392 user 'xxxxxxxxx'
Oct  4 07:30:17 localhost gconfd (xxxxxxxxx-6392): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Oct  4 07:30:17 localhost gconfd (xxxxxxxxx-6392): Resolved address "xml:readwrite:/home/xxxxxxxxx/.gconf" to a writable configuration source at position 1
Oct  4 07:30:17 localhost gconfd (xxxxxxxxx-6392): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Oct  4 07:30:17 localhost gconfd (xxxxxxxxx-6392): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Oct  4 07:30:17 localhost gconfd (xxxxxxxxx-6392): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Oct  4 07:30:20 localhost gconfd (xxxxxxxxx-6392): Resolved address "xml:readwrite:/home/xxxxxxxxx/.gconf" to a writable configuration source at position 0

```

---

### Post by mushr00m on 2006-10-10
damn XGL.

upgrade to EE fixed my problem via allowing me to drop XGL, which was my problem.

---

