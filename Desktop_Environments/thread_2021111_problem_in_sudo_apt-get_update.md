---
title: "problem in sudo apt-get update"
date: 2012-07-08
forum: Desktop Environments
---

### Post by forsubhi on 2012-07-08
I get this error after executing 
sudo apt-get update 

```
Reading package lists... Done
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ precise/main i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by CharlesA on 2012-07-08
Check in software sources to make sure you don't have any duplicate entries.

Otherwise, search for those entries by opening /etc/apt/sources.list in gedit or the like.

---

### Post by forsubhi on 2012-07-09
I get this error instead 
```

W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages  
Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by CharlesA on 2012-07-10
Run this:

```
sudo rm -rv /var/lib/apt/lists/partial/*
```

```
sudo apt-get update
```

---

