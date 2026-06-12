---
title: "Steam won't load under 16.04 VM works fine in 14.04 and SteamOS"
date: 2016-05-19
forum: Gaming &amp; Leisure
---

### Post by KeeperOS on 2016-05-19
I've been experimenting with Virtual Machines via VMWare Workstation and one thing that I have need of testing is Steam.

Under 14.04-based distros (including latest Linux Mint) as well as under SteamOS (Brewmaster, based on Jessie with a smidge of 12.04 thrown in) it works just fine, however, when I try to run it from Xenial (installed from the official repos using apt-get install steam, not through valve) I get the following:

```
Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
[2016-05-19 16:09:31] Startup - updater built Apr 29 2016 22:18:33
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)
```

I've googled the error and most basically suggest updating their (nvidia) drivers but I don't see how that'd be relevant under a Virtual Machine.

Any ideas?

---

### Post by MikeCyber on 2016-05-20
So what? You can't run games in a VM anyway.

---

### Post by KeeperOS on 2016-05-20
Actually you can, both natively and by the use of streaming. But that's not the actual point behind this exercise.

---

### Post by jim_deadlock on 2016-05-23
In theory you can but in practice the limited virtual graphics driver makes the vast majority of games unplayable, either literally because they won't load, or due to extreme video lag. I have to agree with MikeCyber, I wouldn't bother.

---

