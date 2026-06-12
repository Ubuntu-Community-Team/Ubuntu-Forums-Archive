---
title: "Help: klauncher said: Error loading 'kio_file'"
date: 2008-04-03
forum: Desktop Environments
---

### Post by SoloTSi97 on 2008-04-03
For the past couple of weeks, I've been getting a pop-up error message when starting kubuntu 7.10:

Unable to create io-slave
klauncher said: Error loading 'kio_file'

I get the same message when I start up Dolphin and try to browse any of my hard drives.  Some applications appear to run okay (firefox, for exmaple), while others (like azureus) fail to start at all.

I must admit that I'm quite new to Linux, so I'm not well versed in debugging this sort of thing.  I'll try to provide what I suspect may be relevant information, but please do let me know if I can provide info that would be more helpful.

I checked the various files in /var/log.  I didn't see anything of note other than a message that appears in /var/log/apport.log every time that I see the error (when attempting to browse a hard drive in dolphin, for example):

```

apport (pid 28948) Thu Apr  3 21:25:17 2008: called for pid 28946, signal 7
apport (pid 28948) Thu Apr  3 21:25:17 2008: executable: /usr/bin/kdeinit (command line "kio_file\ [kdeinit]\ file\ /tmp/ksocket-bob/klaunchernyIUAa.s")
apport (pid 28948) Thu Apr  3 21:25:17 2008: apport: report /var/crash/_usr_bin_kdeinit.1000.crash already exists and unseen, doing nothing to avoid disk usage DoS

```

The referenced file (/var/crash/_usr_bin_kdeinit.1000.crash) looks basically like a glorified core dump.  I removed that file and recreated the error and found a slightly different message in apport.log:

```

apport (pid 29106) Thu Apr  3 21:43:09 2008: called for pid 29104, signal 7
apport (pid 29106) Thu Apr  3 21:43:09 2008: executable: /usr/bin/kdeinit (command line "kio_file\ [kdeinit]\ file\ /tmp/ksocket-bob/klaunchernyIUAa.s")
modinfo: could not open cdrom: No such device
modinfo: could not open cdrom: No such device
apport (pid 29106) Thu Apr  3 21:43:11 2008: wrote report /var/crash/_usr_bin_kdeinit.1000.crash

```

Any pointers on where to look next would be much appreciated.

-Bob

---

### Post by SoloTSi97 on 2008-04-07
bump

I should point out that I've tried the suggestions that I've found in a few similar threads ... removing /tmp/ksocket-* (and a couple others) and restarting, for example.

Any other suggestions would be appreciated.  If I've posted this in the wrong forum, please move as appopriate ... most of the similar threads I'd seen were in this forum, so I posted here.

Thanks for any assistance!

-Bob

---

