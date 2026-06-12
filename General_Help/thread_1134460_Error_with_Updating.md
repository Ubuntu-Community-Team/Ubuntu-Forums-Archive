---
title: "Error with Updating"
date: 2009-04-23
forum: General Help
---

### Post by mitchbv19 on 2009-04-23
Ive just installed 8.04 and I wanted to try the netbook remix UNR. I am very disatisfied with the addition, and it is causing my Ubuntu to operate differently than previously before. I cant even use update manager because it displays this message. "W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3F2A5EE4B796B6FE"

How do I fix that or revert back to original settings of 8.04 removing UNR. Thanks for your help

---

### Post by drs305 on 2009-04-23
Fix this, you have to add the key. It's a security feature to ensure the package is legitimate:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 3F2A5EE4B796B6FE

```

Here is a link to the Launchpad page giving all the details:
[https://help.launchpad.net/Packaging/PPA#keys?action=show&redirect=PPAKeys]("https://help.launchpad.net/Packaging/PPA#keys?action=show&redirect=PPAKeys")

---

