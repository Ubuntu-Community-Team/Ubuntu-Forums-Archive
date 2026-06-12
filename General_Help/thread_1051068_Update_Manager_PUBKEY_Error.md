---
title: "Update Manager PUBKEY Error?"
date: 2009-01-26
forum: General Help
---

### Post by dwieeb on 2009-01-26
> GPG error: [http://debian-multimedia.org](http://debian-multimedia.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907Failed to fetch [http://debian-multimedia.org/dists/etch/mains/binary-i386/Packages.gz](http://debian-multimedia.org/dists/etch/mains/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Every time Ubuntu says stuff needs to be updated, I run the Check and it downloads 69 package files and then gives me this error. Then, it lists about 10 packages to be downloaded/installed. Those packages install correctly but what about the other packages that it had an error with? Whats going on here?

---

### Post by Vadi on 2009-01-26
You added the [http://debian-multimedia.org](http://debian-multimedia.org) repository but now it's dead, so updating throws an error.

Remove it with System&#8594;Administration&#8594;Software Sources&#8594;Third-party Repositories.

---

