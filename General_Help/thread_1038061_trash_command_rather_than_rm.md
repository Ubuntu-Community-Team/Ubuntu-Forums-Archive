---
title: "trash command rather than rm"
date: 2009-01-12
forum: General Help
---

### Post by MattParkins on 2009-01-12
Like a whole lot of people out there I've written a trash command alias to use from the commandline instead of rm so that I can retrieve files from the trash when I delete the wrong thing, in ~/.bashrc:

alias trash="mv -t ~/.local/share/Trash/files --backup=t --verbose"

The problem is that I use a removable device to store some files on (SDHC), and if I "trash" those ones they take quite some time to go since they are copied to the trash folder on a different device.

Any ideas how to specify the trash folder on the same device as the file I'm trashing?

---

