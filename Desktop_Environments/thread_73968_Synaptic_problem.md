---
title: "Synaptic problem?"
date: 2005-10-10
forum: Desktop Environments
---

### Post by raghav_p on 2005-10-10
ok.. I tried opening synaptic up today and I get this error after it reloaded package information:

```

http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz: 404 Not Found
http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz: 404 Not Found
http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz: 404 Not Found
http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz: 404 Not Found

```

Mind you, this was a fully working apt sources list and I didn't change anything.

Any ideas?

---

### Post by Zelut on 2005-10-10
mirrormax backports are no longer up.  They integrated these into the official ubuntu repositories.  Try this instead:

# backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-backports main universe multiverse restricted

---

### Post by raghav_p on 2005-10-10
worked like a charm! thanks a lot!

---

