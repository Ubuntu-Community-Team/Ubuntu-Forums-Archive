---
title: "System is Corrupt"
date: 2006-12-22
forum: Desktop Environments
---

### Post by dontgetshocked on 2006-12-22
I am having problems with accessing my services either from user or root, it says I am not allowed and I also cannot access users under root as well. Any suggestions? It had said something about hal not being loaded so I re-installed it, this didn't help. Synaptic manager works but thats it.

---

### Post by xabbott on 2006-12-22
Had this exact same thing happen to me today. "Error, failed to initialize Hal"

Do the following...
```

sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12
```

More info at
[https://launchpad.net/distros/ubuntu/+source/dbus/+bug/19577](https://launchpad.net/distros/ubuntu/+source/dbus/+bug/19577)

---

### Post by FlashOmega on 2006-12-22
Wow for an error that scared the crap out of me... that was an easy fix... could the cause have been due to a driver installation?   (cannon printer is the only chance I made) ...

---

### Post by xabbott on 2006-12-23
Not sure. I got it during an update install. Just glad you didnt reinstall or do something drastic to try and fix it. ;)

---

