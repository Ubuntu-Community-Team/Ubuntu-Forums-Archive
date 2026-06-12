---
title: "Unable to update."
date: 2006-09-11
forum: Desktop Environments
---

### Post by bugz0r on 2006-09-11
W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA

This is what it says when I type sudo apt-get update. A similar message is given when i use the Update Manager.

---

### Post by croak77 on 2006-09-12
From that page;

gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys F00175CA
gpg --armor --export F00175CA | sudo apt-key add - 

But this is a debian unstable repo. It may or may not work well with Ubuntu.

---

