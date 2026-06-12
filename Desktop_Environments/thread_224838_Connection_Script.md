---
title: "Connection Script"
date: 2006-07-28
forum: Desktop Environments
---

### Post by Scythe!? on 2006-07-28
Hi, I'm using a USB modem and its quite hit and miss if it connects properly. However, I've messed around a bit and found a command which saves me from rebooting. Can I make a script for my desktop so when i click on it, terminal starts and uses the command:
```
sudo pppd call speedtch
```

I dont mind about bypassing the sudo password, its just a means of remembering the command, but a script would be useful.

---

### Post by roostishaw on 2006-07-28
Yep, I think you can:
```

sudo pppd call speedtch

```
Save that in a text file wherever you'd like. Then make a shortcut with the "Command: " field filled as follows:
```

sh [path to script]

```

---

