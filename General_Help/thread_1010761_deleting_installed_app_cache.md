---
title: "deleting installed app cache?"
date: 2008-12-14
forum: General Help
---

### Post by StOoZ on 2008-12-14
when I use 'apt-get clean' and 'apt-get autoclean' it cleans up the installation packages of the app I installed right (??) , if so , where can I find those (path).

---

### Post by 7raTEYdCql on 2008-12-14
When you install a package using add/remove or synaptic the packages are cached in
"var/cache/apt/archives"

apt-get clean will basically clear all the cached in files and release of space from your root directory.

---

