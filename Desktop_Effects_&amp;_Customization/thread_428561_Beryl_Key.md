---
title: "Beryl Key"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by tyboon on 2007-04-30
Anybody knows where can i find the keys for the indipendent server of beryl..
I got this on my terminal..

W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
hvasss@hvasss-desktop:~$ 

Thanx

---

### Post by jvc26 on 2007-04-30
Try this:
```

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 3FF0DB166A7476EA
gpg --export --armor 3FF0DB166A7476EA | sudo apt-key add -
sudo apt-get update

```
Il

---

### Post by tyboon on 2007-04-30
Thanx a lot ...That worked just fine...
:guitar:

---

