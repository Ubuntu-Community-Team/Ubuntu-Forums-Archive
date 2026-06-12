---
title: "MPlayer fails to play URL"
date: 2007-07-17
forum: Desktop Environments
---

### Post by iXneonXi on 2007-07-17
I cannot play this station. Via Firefox it works but I like having a shortcut to desktop like I do with other mms:// stations. Note: when playing the station it displays a video ad first, and then redirects to the station, but this is the station URL. I don't know if that will affect anything.

I tried asx:
```

<ASX VERSION="3.0">

<ENTRY>

<REF HREF="mms://a490.l2799212489.c27992.g.lm.akamaistream.net/D/490/27992/v0001/reflector:12489" />

</ENTRY>

</ASX>

```
And also this:
```

mplayer -playlist mms://a490.l2799212489.c27992.g.lm.akamaistream.net/D/490/27992/v0001/reflector:12489
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
STREAM_ASF, URL: mms://a490.l2799212489.c27992.g.lm.akamaistream.net/D/490/27992/v0001/reflector:12489
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a490.l2799212489.c27992.g.lm.akamaistream.net
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET...
Connecting to server a490.l2799212489.c27992.g.lm.akamaistream.net[72.246.30.200]: 1755...
Connected
read error:: Operation now in progress
pre-header read failed
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a490.l2799212489.c27992.g.lm.akamaistream.net
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET...
Connecting to server a490.l2799212489.c27992.g.lm.akamaistream.net[72.246.30.189]: 80...
unknown ASF streaming type
Failed, exiting.
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a490.l2799212489.c27992.g.lm.akamaistream.net
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET...
Connecting to server a490.l2799212489.c27992.g.lm.akamaistream.net[72.246.30.200]: 80...
Cache size set to 320 KBytes
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing http://a490.l2799212489.c27992.g.lm.akamaistream.net/D/490/27992/v0001/reflector:12489?MSWMExt=.asf.
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a490.l2799212489.c27992.g.lm.akamaistream.net
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET...
Connecting to server a490.l2799212489.c27992.g.lm.akamaistream.net[72.246.30.189]: 80...
STREAM_ASF, URL: http://a490.l2799212489.c27992.g.lm.akamaistream.net/D/490/27992/v0001/reflector:12489?MSWMExt=.asf
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a490.l2799212489.c27992.g.lm.akamaistream.net
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET...
Connecting to server a490.l2799212489.c27992.g.lm.akamaistream.net[72.246.30.200]: 80...
unknown ASF streaming type
Failed, exiting.
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET6...
Couldn't resolve name for AF_INET6: a490.l2799212489.c27992.g.lm.akamaistream.net
Resolving a490.l2799212489.c27992.g.lm.akamaistream.net for AF_INET...
Connecting to server a490.l2799212489.c27992.g.lm.akamaistream.net[72.246.30.200]: 80...
Cache size set to 320 KBytes
Cache fill:  0.06% (196 bytes)   


Playing http://72.246.30.200:80/D/490/27992/v0001/reflector:12489?MSWMExt=.asf.
Resolving 72.246.30.200 for AF_INET6...
Couldn't resolve name for AF_INET6: 72.246.30.200
Connecting to server 72.246.30.200[72.246.30.200]: 80...
STREAM_ASF, URL: http://72.246.30.200:80/D/490/27992/v0001/reflector:12489?MSWMExt=.asf
Resolving 72.246.30.200 for AF_INET6...
Couldn't resolve name for AF_INET6: 72.246.30.200
Connecting to server 72.246.30.200[72.246.30.200]: 80...
unknown ASF streaming type
Failed, exiting.
Resolving 72.246.30.200 for AF_INET6...
Couldn't resolve name for AF_INET6: 72.246.30.200
Connecting to server 72.246.30.200[72.246.30.200]: 80...
Cache size set to 320 KBytes
Cache fill:  0.05% (164 bytes)   


Exiting... (End of file)


```

104.1 The Rock of New Orleans KYRK-FM (Streaming)
mms://a490.l2799212489.c27992.g.lm.akamaistream.net/D/490/27992/v0001/reflector:12489
mms://a490.l2799212489.c27992.g.lm.akamaistream.net/D/490/27992/v0001/reflector:12489?auth=caEcrdVbrbDalaAaLc9azcOdNd2arbmcdbq-bgNn8V-4q-SO4W7_anmDGnt3DAslvuFs&aifp=1234&CPROG=SIMULCAST&MARKET=NEWORLEANS-LA&MNM=2&NG_FORMAT=activerock&NG_ID=KYRK1041FM&OR_NEWSFORMAT=&RVN_TZ=-6&SERVER_NAME=therockofneworleanscom&SITE_ID=4041&STATION_ID=KYRK-FM

---

