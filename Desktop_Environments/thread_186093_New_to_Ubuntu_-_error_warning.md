---
title: "New to Ubuntu - error warning"
date: 2006-06-01
forum: Desktop Environments
---

### Post by kettlehead on 2006-06-01
Hi all

I'm new to ubuntu so having lots of fun and managing to survive all tasks so far...I think.  A great experience anyway.

My problem (if it is a problem) is that when I open the Synaptic Packge Manager I get the following warning.   The question is what is it, what can I do about it, where can I find documentation about this warning and is it "life" threatening?

[I]W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)[/I]

---

### Post by Jussi Kukkonen on 2006-06-01
Not serious, in fact not a problem on your computer at all. The updated package lists just weren't found on the server-- I wouldn't be surprised if the Dapper release and the hordes of downloaders had something to do with it.

Try again another day, if the problem still persists you can try other servers -- like removing **au.** from [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com).

EDIT: Oh yeah, documentation:
```
man sources.list
```

---

