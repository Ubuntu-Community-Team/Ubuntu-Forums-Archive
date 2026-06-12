---
title: "Public key??"
date: 2006-08-08
forum: Desktop Environments
---

### Post by Daandaan on 2006-08-08
When I start my update manager I get the following error:

W: GPG error: [http://debian.space-based.de](http://debian.space-based.de) experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EB020D4677AFC5B7

Does anyone know what to do about this?

Greetz Daan

---

### Post by matko on 2006-08-08
this is due security. that means you (or somebody else) cant install from unrusted source. 

but you can tell your box to accept software frm this source by importing GPG (Public Key). 

yoyu accept key by this
downlaod key:
```
gpg --keyserver subkeys.pgp.net --recv-keys 77AFC5B7
```
import key:
```
gpg --export --armor 77AFC5B7 | sudo apt-key add -
```

---

### Post by dyrer on 2006-10-22
I still have problem with public key on [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper

---

### Post by Kateikyoushi on 2006-10-22
Use the same command just replace the key.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -

```

---

