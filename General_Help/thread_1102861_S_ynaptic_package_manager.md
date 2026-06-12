---
title: "S ynaptic package manager"
date: 2009-03-22
forum: General Help
---

### Post by mohitagnihotri on 2009-03-22
Hi all,
i am facing problem while running the package manager.
following errors pop up.
any solution.........................


E: Problem parsing dependency Depends
E: Error occurred while processing qwebmail (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

### Post by snova on 2009-03-22
Try:

```
sudo apt-get update
```

In the terminal.

---

