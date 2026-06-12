---
title: "What this mean?"
date: 2009-03-20
forum: General Help
---

### Post by azmo35 on 2009-03-20
:(In synaptic i get this ```
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828
``` what this mean many thanks,azmo

---

### Post by albandy on 2009-03-20
simply that you added a new repository without adding the gpg key.

---

### Post by sisco311 on 2009-03-20
You need update your Launchpad PPA repositories and apt keys.

If you have more then one PPA repo you can use [thread=1056099]this[/thread] script.


Or:
```
gpg --keyserver keyserver.ubuntu.com --recv **40130828**
```
```
gpg --export --armor **40130828** | sudo apt-key add -
```
```
sudo apt-get update
```

**40130828** - the last 8 digits from the warning message.

---

### Post by azmo35 on 2009-03-20
Thanks sisco311 that solve the problem i used the code in terminal,cheers azmo.

---

