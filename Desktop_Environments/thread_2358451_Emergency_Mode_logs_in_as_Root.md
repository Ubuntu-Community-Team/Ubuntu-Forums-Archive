---
title: "Emergency Mode logs in as Root"
date: 2017-04-13
forum: Desktop Environments
---

### Post by scpatl4now on 2017-04-13
I was having a problem where I tried to open firefox and got error that it was already running, so I logged off.  When I tried to log back on it kept going back to the login screen.  I rebooted and get to

Welcome to Emergency Mode!  After logging in type journalctl -xb

If I hit enter, instead of asking me to log in, I'm logged in as ROOT!

This doesnt look right at all and I cant get past this screen other than to type the entry and look at logs which dont tell me much.  This is 16.04, but I also have 14.04 on another partition which I was able to boot up to and used bootrepair to get this system info
paste.ubuntu.com/24375995
I'm not sure what to do, but doing it as root by default seems a bit on the risky side

---

### Post by scpatl4now on 2017-04-13
Not sure what I did, but was able to boot to recovery and chose to fix broken packages and was able to log in again...so I guess this is solved

---

