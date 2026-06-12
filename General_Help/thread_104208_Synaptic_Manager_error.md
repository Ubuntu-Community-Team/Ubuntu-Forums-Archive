---
title: "Synaptic Manager error"
date: 2005-12-15
forum: General Help
---

### Post by ninocass on 2005-12-15
hi all, im getting this error when i start the stnaptic manager:

```

W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```

thanks

---

### Post by earobinson on 2005-12-15
this means that you need to remove (or the sources are temporaly down) those sources from your sources.list (they are broken and your computer cant connect to them so its telling you so)

---

### Post by ninocass on 2005-12-15
where is the sources located?

---

### Post by earobinson on 2005-12-15
lol you edited them before /etc/apt/sources.list

this question could have also been answered by searching the forums for sources.list

---

### Post by aysiu on 2005-12-15
See the first link in my sig.

---

