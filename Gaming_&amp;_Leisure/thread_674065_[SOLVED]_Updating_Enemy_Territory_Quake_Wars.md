---
title: "[SOLVED] Updating Enemy Territory: Quake Wars"
date: 2008-01-21
forum: Gaming &amp; Leisure
---

### Post by BOZG on 2008-01-21
I just tried to update from v1.2 to v1.4 but I can't get it to install.  I downloaded the update patch within the game but try to install it the installation folder at /usr/local/games/etqw but I get a mkdir failure all the time.  I've been unable to find a standalone update patch and can only find v1.4 full clients.  Can anyone help?

---

### Post by Ozor Mox on 2008-01-21
I had the same problem. It's because the updater launches itself as a normal user, not as root, so it does not have permissions to create the directories it wants. Start the installer manually from where it was downloaded to by doing

```
sudo ./(installer)
```

I think it puts it in your home folder, it should tell you.

---

### Post by BOZG on 2008-01-22
Thanks a lot.  I figured that out eventually and forgot about the thread here.

---

