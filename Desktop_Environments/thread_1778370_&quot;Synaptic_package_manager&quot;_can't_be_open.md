---
title: "&quot;Synaptic package manager&quot; can't be opened"
date: 2011-06-08
forum: Desktop Environments
---

### Post by AaronChee on 2011-06-08
Whenever I open "Synaptic Package manger", it always pops up this eroor massage:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/tw.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

Could anyone possibly help me with the trouble, THX^^

---

### Post by dFlyer on 2011-06-08
What happens when you run sudo apt-get update from the command line?

---

### Post by garvinrick4 on 2011-06-09
Open a terminal ctrl/alt/t
and copy and paste these one at a time:
```

sudo rm /var/lib/apt/lists/* -vf 
sudo apt-get clean all 
sudo apt-get update

```

---

