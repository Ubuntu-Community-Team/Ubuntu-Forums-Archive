---
title: "Errors in Synaptic and apt-get."
date: 2006-01-18
forum: General Help
---

### Post by Age One on 2006-01-18
when I try and run synaptic I get these errors.

```
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-amd64_Packages) - stat (2 No such file or directory)

```

also, I don't know if its related or not, but search engines like google or yahoo don't work and its making things difficult.:???

---

### Post by jsmidt on 2006-01-18
Often you get that when the server hiccops.  Sometimes you just have to wait a while and try to reload again.

You can also open a terminal and type as root:
```

apt-get update

```

Sometimes the terminal workes best

If it is an upgrade error try typing in terminal

```

apt-get -f upgrade

```

That often does the trick.

ps  You log into root by typing in a terminal
```

sudo -s -H

```
and giving your password

---

