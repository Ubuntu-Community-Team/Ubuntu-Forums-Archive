---
title: "Mono?"
date: 2008-12-22
forum: General Help
---

### Post by Grant A. on 2008-12-22
Does xubuntu have mono by default?

---

### Post by beno1990 on 2008-12-22
I just checked the dependencies of the xubuntu-desktop metapackage on Synaptic and it doesn't list mono as a dependency.

It's easy to install, though.

```

sudo apt-get install mono

```

from within Xubuntu.

---

### Post by directhex on 2008-12-23
> **beno1990 said:**
> I just checked the dependencies of the xubuntu-desktop metapackage on Synaptic and it doesn't list mono as a dependency.

It's easy to install, though.

```

sudo apt-get install mono

```

from within Xubuntu.

Nope, the "mono" metapackage died a few years ago.

If you want to do Mono development, install "mono-2.0-devel" on 8.* or "mono-devel" on 6.*, 7.*, 9.*

---

