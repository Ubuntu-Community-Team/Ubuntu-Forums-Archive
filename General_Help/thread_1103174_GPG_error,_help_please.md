---
title: "GPG error, help please"
date: 2009-03-22
forum: General Help
---

### Post by umbc_brian on 2009-03-22
As of recently, I've been getting GPG errors when running Update Manager, saying there is no public key available, I went into the repository's and tried to find the exact launchpad that is getting the GPG error, and using "#" to comment it out, but I can't seem to find it, does anyone know a fix for this?

*Running 8.10


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0BF0F083E353B3E9

---

### Post by taurus on 2009-03-22
[https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA](https://help.launchpad.net/Packaging/PPA?action=show&redirect=PPA)
[http://ubuntuforums.org/showthread.php?t=1047743](http://ubuntuforums.org/showthread.php?t=1047743)

---

### Post by chriskin on 2009-03-22
or more easily :

> **taavikko said:**
> This is for the first key,

```
gpg --keyserver keyserver.ubuntu.com --recv 0c713da6
``````
gpg --export --armor 0c713da6 | sudo apt-key add -
```Do the same for the other key...
Last 8 digits...

Probably good idea to tell the problem to owner of ppa?

as said , use the 8 last digits instead of the ones in the example above

---

