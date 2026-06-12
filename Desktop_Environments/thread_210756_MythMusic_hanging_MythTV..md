---
title: "MythMusic hanging MythTV."
date: 2006-07-07
forum: Desktop Environments
---

### Post by denisesballs on 2006-07-07
I've compiled MythTV and MythPlugins 0.19 for Ubuntu Dapper, and
everything works great, except it seems to hang when accessing MythMusic.
If I don't have MythMusic installed, MythTV starts immediately. If I do,
on startup I have exactly a 22 second delay between MythDVD and MythMusic:

2006-07-07 09:09:37.732 Registering MythDVD VCD Media Handler as a media
handler
2006-07-07 09:09:59.206 Registering MythMusic Media Handler as a media
handler

It really hangs the startup. If I use verbose output I see the delay here:

2006-07-07 09:11:53.034 Enabling Settings Cache.
2006-07-07 09:11:53.034 Clearing Settings Cache.
2006-07-07 09:12:14.385 MSqlQuery: SELECT data FROM settings WHERE value =
'MusicLocation' AND hostname = 'Koerner';

Anyone you have any idea what is happening here? Again the only problem is the MythMusic. Any help is GREATLY appreciated! Thanks!

---

