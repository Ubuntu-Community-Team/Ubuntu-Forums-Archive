---
title: "On remote reboot, bypass KDE daemon kwalletmanager"
date: 2011-01-03
forum: Desktop Environments
---

### Post by tarahmarie on 2011-01-03
I tried a remote reboot via ssh. I couldn't log back in even though sshd is a startup script, because the KDE daemon wanted me to enter my kwallet password...which is of course part of the DE, not something accessible via ssh.  How do I turn off that check or automate it?

---

### Post by Zorael on 2011-01-03
Set your wallet to have a blank password. :3

Additionally you'll have to make sure to allow the network manager to access it, but I'd imagine you've allowed it already.

---

### Post by tarahmarie on 2011-01-03
> **Zorael said:**
> Set your wallet to have a blank password. :3

Additionally you'll have to make sure to allow the network manager to access it, but I'd imagine you've allowed it already.

That fixed it. Thanks!

---

