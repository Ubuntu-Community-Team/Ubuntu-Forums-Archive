---
title: "Synaptic problem"
date: 2005-04-30
forum: Desktop Environments
---

### Post by samppi on 2005-04-30
In Synaptic, I'm trying to "reload the package information". But it comes up with the following error:

W: GPG error: [http://http.us.debian.org](http://http.us.debian.org) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D

Does anyone know how to fix this?

---

### Post by cdhotfire on 2005-04-30
try
```

$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys F1D53D8C4F368D5D
$ gpg --armor --export 1F41B907 | sudo apt-key add -
$ sudo apt-get update


```

dont know if this will work, but should.:-P

---

### Post by samppi on 2005-05-01
Thanks, but unfortunately, that doesn't work. (When I enter line 2 of the code, it says that the gpg exported nothing.) Any more suggestions?

---

### Post by cdhotfire on 2005-05-01
oops,:|

```

$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys F1D53D8C4F368D5D
$ gpg --armor --export F1D53D8C4F368D5D | sudo apt-key add -
$ sudo apt-get update 
```

hehe:smile:

---

