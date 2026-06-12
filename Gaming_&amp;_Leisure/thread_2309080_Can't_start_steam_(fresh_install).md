---
title: "Can't start steam (fresh install)"
date: 2016-01-07
forum: Gaming &amp; Leisure
---

### Post by b3nlusty on 2016-01-07
Hi there, complete newbie to linux and ubuntu here, tried to install steam using the software centre (after some problems tried the website too) and can't get it to start. I did get to the terms and conditions type thing you have to accept once but nothing further has happened.

When I type steam in terminal I get:

ben@ben-H81M-D2V:~$ steam
Running Steam on ubuntu 14.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
libGL error: unable to load driver: nouveau_dri.so
libGL error: driver pointer missing
libGL error: failed to load driver: nouveau
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast


Can't find a solution anywhere, but I'm probably just dumb. Can anyone help?

---

### Post by b3nlusty on 2016-01-07
UPDATE

After trying to install again I encountered an error message that took me to [https://bugs.launchpad.net/ubuntu/+source/steam/+bug/1300434](https://bugs.launchpad.net/ubuntu/+source/steam/+bug/1300434)

As lots of messages here say, uninstalling what existed and installing through terminal (sudo apt-get install steam) worked perfectly! Hope this helped anyone (Ubuntu 14.04 LTS)

---

