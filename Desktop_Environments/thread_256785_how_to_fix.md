---
title: "how to fix?"
date: 2006-09-13
forum: Desktop Environments
---

### Post by bugz0r on 2006-09-13
W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signaturescouldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA
W: You may want to run apt-get update to correct these problems

---

### Post by skymt on 2006-09-13
Run the following two commands in a terminal:```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F00175CA
gpg --armor --export F00175CA | sudo apt-key add -
```These commands were copy-pasted directly from [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/).

---

