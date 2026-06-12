---
title: "Lightning add-on (thunderbird) and default keyring"
date: 2008-12-23
forum: Desktop Environments
---

### Post by weryl on 2008-12-23
Hi,

I've just reinstalled ubuntu after a few months of Vista+XP and I'm having the following problems:

1. On thunderbird, I just can't get lightning to work properly. I've tried installing it manually (through thunderbird) and automatically (Add/Remove program) but in both case I can't create events, tasks or even a new calendar.

2. Every time I reboot I get prompted for a password for my default keyring to log in to the wireless network. Can I disable that?

Thanx alot,

---

### Post by Astro96 on 2008-12-26
To fix lightning you probably need to install libstdc++5 or libstdc++6 or both -- I can't remember which one right now:

```

sudo apt-get install libstdc++5 libstdc++6

```


Andy

---

