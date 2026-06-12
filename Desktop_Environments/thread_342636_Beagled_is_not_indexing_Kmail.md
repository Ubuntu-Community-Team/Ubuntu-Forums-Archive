---
title: "Beagled is not indexing Kmail"
date: 2007-01-20
forum: Desktop Environments
---

### Post by pqs on 2007-01-20
Hello,

Beagle is not indexing my Kmail e-mails.

When launching beagled -fg I get a warning:



```

pqs@quintana:~$ beagled --fg
Debug: Starting Beagle Daemon (version 0.2.9)
Debug: Running on Mono 1.1.17.1
Debug: Command Line: /usr/lib/beagle/BeagleDaemon.exe --fg
Debug: Established a connection to the X server
Debug: Starting main loop
Debug: Beginning main loop
Debug: Starting messaging server
Debug: Starting QueryDriver
Debug: Found index helper at /usr/lib/beagle/beagled-index-helper
Debug: Found 1 backends in /usr/lib/beagle/Backends/ThunderbirdBackends.dll
Warn: KMail backend: /home/pqs/.kde/share/apps/kmail/mail contains a maildir directory but no corresponding index file. Probably not a KMail mail directory. Ignoring this location!
Warn: KMail backend: /home/pqs/.kde/share/apps/kmail/mail contains a maildir directory but no corresponding index file. Probably not a KMail mail directory. Ignoring this location!
Debug: KMail folders not found. Will keep trying
Debug: Starting Inotify Backend
Debug: KonqCacheDir: /var/tmp/kdecache-pqs/http
Debug: Found 10 backends in /usr/lib/beagle/BeagleDaemonLib.dll
Debug: Reading mapping from filters
Debug: Loading system static indexes.
Debug: Found 0 system-wide indexes.
Debug: Loading user-configured static indexes.
Debug: Found 0 user-configured static indexes..
Debug: Waiting 60 seconds before starting queryables
Debug: Starting Scheduler thread
Debug: Starting Inotify threads
Debug: Daemon initialization finished after ,96s
```

I'm using Kmail normally and it works fine. So I don't understand why beagled would'nt understand its files.

Does anybody know how could I solve this problem?

Thank You!

---

