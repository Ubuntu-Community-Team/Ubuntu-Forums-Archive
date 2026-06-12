---
title: "backport errors."
date: 2005-10-13
forum: Desktop Environments
---

### Post by Adam Lee on 2005-10-13
Is this the server problem?
I simply added to the repository according to the 5.10 guide from the help file.

```
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
```

---

### Post by darkmatter on 2005-10-13
Adam, just comment out those lines. Backports for Breezy have not yet been brought on line.

---

### Post by Adam Lee on 2005-10-13
Oh, I see.. 
Thx!

---

