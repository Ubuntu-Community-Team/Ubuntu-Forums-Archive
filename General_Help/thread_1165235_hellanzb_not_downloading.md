---
title: "hellanzb not downloading"
date: 2009-05-20
forum: General Help
---

### Post by satman-ga on 2009-05-20
I recently loaded Netbook Remix on my new netbook. I've installed hellnzb from the repos and cannot get it fully working. Whenever I add a new nzb it gets queued, but does not start downloading. My first thought was that it was a config issues, so I compared the config against a previously working config on another machine. No dice. When I tried to verify that hellanzb worked on the other machine it fails in the same manner(it's been months since I used that one).


I have tried the fixes listed here:
[http://www.hellanzb.com/trac/hellanzb/ticket/393#comment:6](http://www.hellanzb.com/trac/hellanzb/ticket/393#comment:6)

hellanzb displays the following
```
hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
(Giga) Opening 5 connections...
hellanzb - Now monitoring queue...
Found new nzb: 24-7x23
Downloading: 24-7x23
Parsing: 24-7x23.nzb...
Parsed: 35 files (1067 posts), 401.8MB
Queued: 401.8MB
[1]
[2]
[3]
[4]
[5]
[Total] 0.0KB/s, 401 MB queued, ETA: 00:00:00
```

I started hellanzb using 'hellanzb -d ~/helladebug'. The file contains

```
2009-05-20 12:47:22,001 hellanzb v0.13 (config = /etc/hellanzb.conf, C yenc module)
2009-05-20 12:47:22,073 Using: Twisted-8.2.0, TwistedWeb-8.2.0
2009-05-20 12:47:22,074 python: 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
2009-05-20 12:47:22,075 [GCC 4.3.3]
2009-05-20 12:47:22,076 os: Linux-2.6.28-11-generic (i686)
2009-05-20 12:47:22,076 initFillServers: fillserver support disabled
2009-05-20 12:47:22,102 recoverStateFromDisk recovered: RecoveredState: version: 0.13 newzbinCookie keys: []
downloading: {}
processing: {}
queued: {}
2009-05-20 12:48:07,531 stdinEchoOff - OFF
```

I've verified that the nzb files are good and my server login credentials are good using newsbin pro in windows. I'm at a loss since the old, previously working install does not work either.

---

