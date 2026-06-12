---
title: "need help with installation LogitechMediServer"
date: 2012-05-14
forum: Desktop Environments
---

### Post by SuperFreak on 2012-05-14
I had problems with LogitechMediaServer connecting so I unistalled the program. Now I am not able to reinstall it. When I try reinstalling this 250MB program Software Centre takes about 3 seconds then marks it not as installed but for reinstall. I tried removing and reinstalling through synaptic also to not avail

I also tried solution at [http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

```
cd /var/lib/dpkg/info
sudo rm logitechmediaserver.*

sudo dpkg --remove --force-remove-reinstreq logitechmediaserver
```

Foolishly I deleted some files in the root directory that were marked squeezeboxserver

Any help would be greatly appreciated

---

### Post by SuperFreak on 2012-05-14
Mysteriously the problem has resolved itself. I have LogitechMediaServer running now although it no longer appears in Software Center

---

