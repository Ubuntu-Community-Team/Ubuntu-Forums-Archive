---
title: "Synaptic error"
date: 2005-05-03
forum: Desktop Environments
---

### Post by samppi on 2005-05-03
I've just added the Universe repository with Synaptic, but when I try to reload the packages' information, it comes with the following error:

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

How can I fix this?

---

### Post by cdhotfire on 2005-05-03
```

$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 07DC563D1F41B907
$ gpg --armor --export 07DC563D1F41B907 | sudo apt-key add -
$ sudo apt-get update

```

i think that should do it.:)

---

### Post by samppi on 2005-05-04
When I try to do "gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 07DC563D1F41B907", it says the following errors:

gpg: can't open `/home/joshua/.gnupg/pubring.gpg'
gpg: keydb_get_keyblock failed: eof
gpg: no writable keyring found: eof
gpg: error reading `[stream]': general error
gpg: Total number processed: 0

So, when I try to do "gpg --armor --export 07DC563D1F41B907 | sudo apt-key add -", it says that gpg has exported nothing.

---

### Post by cdhotfire on 2005-05-04
check your permissions on /home/joshua/.gnupg/pubring.gpg
try
```

$ sudo chown joshua:joshua /home/joshua/.gnupg/pubring.gpg

```

then try the other command again.:)

---

