---
title: "Update Manager is borked"
date: 2009-01-03
forum: General Help
---

### Post by the real omni on 2009-01-03
Update Manager has the little orange icon in my notification area. I double-click on it, the Update Manager window appears, then immediately gives me this error dialog:


Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:Error occurred while processing librvm-dev (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_hardy_universe_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by taurus on 2009-01-03
Close the update-manager window.  Then, open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

---

### Post by ByKeLaO on 2009-01-03
Try opening up Synaptic (System->Administration->Synaptic Package Manager) and see if you get the same error. If it works OK, reload the package list, click Mark All Upgrades and then click Apply to install updates from there.
EDIT: Looks like I was beaten to it

---

