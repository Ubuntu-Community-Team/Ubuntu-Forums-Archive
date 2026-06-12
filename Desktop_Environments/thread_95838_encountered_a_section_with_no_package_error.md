---
title: "encountered a section with no package error"
date: 2005-11-27
forum: Desktop Environments
---

### Post by sevenrechlin on 2005-11-27
Hello, I'm getting a weird problem when I try to run synaptic or apt-get.

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I've looked in other forum posts and found the command "sudo dpkg --clear-avail" but it didn't work or seem to do anything.  the status file is huge and I would guess I shouldn't be messing with it by myself :p.

---

### Post by Xian on 2005-11-27
It sounds like your /var/lib/dpkg/status file is corrupted. There is a backup called status-old in the same path that you can replace it with (or look for diffs and merge), or if that doesn't work there are some older backups in /var/backups/dpkg.status.*

---

### Post by sevenrechlin on 2005-11-27
I will try that in a bit...  One question though, will that screw up any other packages that were installed around the time that whichever one was installed that is giving me the error?  Taking a quick look at my status-old file, I can see that it's a bit smaller than my normal one...

---

### Post by az on 2005-11-27
You should start off fresh with

sudo dpkg --clear-avail

No, it should not screw up any unconfigured packages.  Not any more than doing apt-get update would.

---

### Post by Xian on 2005-11-27
It won't affect the actual package installation but there might be some residual information issues regarding how the package manager interprets what exists on the system. However, I am not aware of any other alternative.

---

### Post by sevenrechlin on 2005-11-27
Ok and I tried sudo dpkg --clear-avail but it didn't work, I still get that error... And the file size of "status" is 1.5mb if thats odd.

---

