---
title: "WoW Help needed!"
date: 2007-06-30
forum: Gaming &amp; Leisure
---

### Post by forublink182 on 2007-06-30
Hi,
I just recently switched to Ubuntu and I'm learning how to use it all. I was wanting to download WoW using the wowclient-downloader.exe through wine. Only problem is... it won't let me use the client for some reason.

Here's what the terminal is giving me when I go to run the client from wine /home/shawn/Desktop/wowclient-downloader.exe :

shawn@sjd-hdd:~/Desktop$ wine wowclient-downloader.exe
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: could not find DOS drive for current working directory '/home/shawn/Desktop', starting in the Windows directory.
wine: could not load L"c:\\windows\\system32\\wowclient-downloader.exe": Module not found


Can anyone help me with this error?

If so, THANK YOU in advance!

-Shawn

---

### Post by hikaricore on 2007-06-30
You need to run:

```
winecfg
```

From a terminal before attempting to run anything with wine.

---

### Post by forublink182 on 2007-07-01
I ran it before. I think there was a problem with my Ubuntu install. So i wiped the drive and started over. Seems to have fixed the problem with wine. Thank you though!

---

