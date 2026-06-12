---
title: "Upgrading Gnome on Ubuntu 8.04 LTS"
date: 2010-02-10
forum: Desktop Environments
---

### Post by Nrip Cheema on 2010-02-10
Is it possible to upgrade gnome 2.22.3 to latest version 2.28 on Ubuntu 8.04 LTS

---

### Post by tripolitan on 2010-02-10
It is not in the 8.04 Backports repository. Since there is not much difference from 2.22, I would wait two more months for the next LTS, which will have 2.28.

The problem is the dependencies of 2.28, a quick test would be to enable Lucid repositories (at your own risk), apt-get update then, using synaptic, once you select gnome to be upgraded, see if the dependencies are solved, without breaking your LTS install.

Myself, I have never been successful mixing and matching stable and unstable software. Good luck.

---

