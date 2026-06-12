---
title: "Installing ClamAV"
date: 2006-07-22
forum: Desktop Environments
---

### Post by jazzman14 on 2006-07-22
When I install it, after i run the ./configure, I get:

configure: error: User clamav (and/or group clamav) doesn't exist. Please read the documentation !

any solutions?

---

### Post by lamego on 2006-07-22
kenascher,
clamav is available from the repositories, go the the package manager and install it.

If you really don't know what that message means you shouldn't be trying to compile it.

The message is pretty clear, you need a clamav user and group on the system.

---

