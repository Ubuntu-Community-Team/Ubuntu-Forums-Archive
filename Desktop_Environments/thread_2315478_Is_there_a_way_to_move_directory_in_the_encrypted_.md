---
title: "Is there a way to move directory in the encrypted home to a second disk and keep the"
date: 2016-02-29
forum: Desktop Environments
---

### Post by arthur.lutz on 2016-02-29
I have an install with home encryption (ecryptfs), it works fine, but am running out of space on that first disk, I have a second disk plugged in and formatted to ext4. Is it possible to use the same mechanism used by the encrypted home (pam+unlock-passphrase+mount) for some folders on that disk, for example Images. I want to avoid having to type a password twice. If possible I would like to avoid an encrypted file-system since there will probably be multiple users.

Am looking into customizing ecryptfs-setup-private, but if there is a simpler way, thanks for pointing to it !

---

