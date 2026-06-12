---
title: "Dolphin: &quot;klauncher said: Unknown Protocol 'file'&quot;"
date: 2011-12-20
forum: Desktop Environments
---

### Post by yoramdavid on 2011-12-20
Hello all,

I am in Ubuntu 11.10 gnome-classic desktop.
I have an issue with dolphin.
All of the sudden it stopped displaying files and folders.
The error it returns is the following:
```
It was not possible to start the process. It was not possible to create an 'ioslave':
klauncher said: Unkown Protocolo 'file'
```

Perhaps a better translation would be:
```
Could not start process. Unable to create an 'isoslave'
klauncher said: Unkown Protocolo 'file'
```

Any idea why this is happening? Some updates took place for KDE.

---

### Post by kjaertaker on 2011-12-20
I had the problem today also after the update. Try rebooting, the update replaced several pf the kdepim libs, etc... rebooting will allow kde to pick up those changes.

---

### Post by yoramdavid on 2011-12-21
> **kjaertaker said:**
> I had the problem today also after the update. Try rebooting, the update replaced several pf the kdepim libs, etc... rebooting will allow kde to pick up those changes.

Yes, it was fine after reboot.
Thanks kjaertaker

---

