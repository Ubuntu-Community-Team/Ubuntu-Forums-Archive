---
title: "need help with PUBKEY"
date: 2009-04-15
forum: General Help
---

### Post by SchindlerShadow on 2009-04-15
keep getting this when i try to update, help? :(

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC66403D8670A035

---

### Post by zvacet on 2009-04-15
In terminal type 

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys  FC66403D8670A035
gpg --export --armor  FC66403D8670A035 | sudo apt-key add -
```

---

### Post by SchindlerShadow on 2009-04-15
Hey thanks! :p:p:p

---

### Post by Teber on 2009-04-27
thanks zvacet. i had this similar problem. your solution worked just fine under hardy too.

:)

---

