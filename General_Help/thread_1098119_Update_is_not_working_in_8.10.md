---
title: "Update is not working in 8.10"
date: 2009-03-16
forum: General Help
---

### Post by 73ckn797 on 2009-03-16
I suddenly cannot get the latest updates to install. The notification icon appears. The usual window opens and lists the available updates. When I select to install nothing happens.
There are no error messages that display.

Any ideas? Did the last update mess something up?

---

### Post by taurus on 2009-03-16
Have you tried it from a terminal?  Of course, you need to close down the update manager first.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by 73ckn797 on 2009-03-16
> **taurus said:**
> Have you tried it from a terminal?  Of course, you need to close down the update manager first.

```
sudo apt-get update
sudo apt-get upgrade
```

I have been getting the GPG key error for Launchpad. My searching has been an exercise in futility. No clear info is given.

The error has been ongoing before this current problem. Could it be that the updates are all from Launchpad? I doubt that. They appear to be normal security and recommended updates.

Here is the error for Launchpad:
```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: You may want to run apt-get update to correct these problems
```

---

### Post by taurus on 2009-03-16
[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA)

---

### Post by 73ckn797 on 2009-03-16
taurus,

I disabled Open Office and Ubuntu Tweak in Software Sources and was able to run the terminal commands to install the updates. Those two are Launchpad sources. I will have to work on getting the keys a little later.

Thanks.

---

### Post by forger on 2009-03-17
use this perl script: 
[http://ubuntuforums.org/showthread.php?t=1056099](http://ubuntuforums.org/showthread.php?t=1056099)

---

