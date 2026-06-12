---
title: "error adding MATE to Ubuntu 13.10"
date: 2014-02-21
forum: Desktop Environments
---

### Post by neel3 on 2014-02-21
Commands:
```
sudo add-apt-repository "deb http://repo.mate-desktop.org/ubuntu saucy main"
sudo apt-get update

```
Result:
> Fetched 1,293 kB in 58s (22.0 kB/s)
Reading package lists... Done
W: GPG error: [http://repo.mate-desktop.org](http://repo.mate-desktop.org) saucy InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 68980A0EA10B4DE8


---

### Post by buzzingrobot on 2014-02-21
You need to download and install the Mate keyring and rerun the update.

Closely follow the install instructions for 13.10 located here:  [http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download) and you'll be good.

---

