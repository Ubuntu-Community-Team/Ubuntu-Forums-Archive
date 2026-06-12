---
title: "Error when I check for updates"
date: 2009-03-13
forum: General Help
---

### Post by CoreyB. on 2009-03-13
Whenever I check for updates with Update Manager, I get this error:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 39456311108B243F

How do I fix this?

---

### Post by kanikilu on 2009-03-13
[http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by CoreyB. on 2009-03-13
The problem is with this source:

[https://launchpad.net/~ssakar/+archive/ppa](https://launchpad.net/~ssakar/+archive/ppa)

I click on the link for the key, and nothing happens, it doesn't go to the page with all of the text on it.

---

### Post by kanikilu on 2009-03-13
Try: ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com c6e3d905c8bcd56bb02e6e0b39456311108b243f
```

---

### Post by CoreyB. on 2009-03-13
> **kanikilu said:**
> Try: ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com c6e3d905c8bcd56bb02e6e0b39456311108b243f
```

Brilliant, thanks kanikilu, that did the trick!

---

