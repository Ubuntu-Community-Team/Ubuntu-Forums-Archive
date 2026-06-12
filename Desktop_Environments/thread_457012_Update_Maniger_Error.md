---
title: "Update Maniger Error"
date: 2007-05-28
forum: Desktop Environments
---

### Post by Magiczero on 2007-05-28
hi

This morning I turned my computer on & it said there were updates to do so i clicked the button & got this error.
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing thekompany-support (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I have never seen this message before...  Can anyone help me?

Thanks

---

### Post by guice on 2007-05-28
Remove this file: /var/lib/apt/lists/www.getautomatix.com_apt_dists_feisty_main_binary-i386_Packages

And then redo the update.

---

### Post by Magiczero on 2007-05-28
How?

---

### Post by Koutroumpesis on 2007-05-28
login as root. pen the filesystem and do the rests
thanxxx ;) now it works

---

