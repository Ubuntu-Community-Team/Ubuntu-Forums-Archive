---
title: "Synaptic Package Manager error"
date: 2005-08-07
forum: Desktop Environments
---

### Post by Hig on 2005-08-07
When I start my Synaptic Package Manager I get the following error:
```
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/main Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/universe Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/multiverse Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://backports.ubuntuforums.org hoary-extras/restricted Packages (/var/lib/apt/lists/backports.ubuntuforums.org_backports_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```

I tried searching but kept getting 'too long, short, or common' errors.

EDIT: Just removed them from the manager window.

---

### Post by grj on 2005-08-07
it appears your sources.list file is not correct. You may be missing this behind the .org

/ubp

---

