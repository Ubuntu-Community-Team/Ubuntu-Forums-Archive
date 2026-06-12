---
title: "it takes 10 seconds to ls in my home directory"
date: 2009-01-22
forum: General Help
---

### Post by RedWagon on 2009-01-22
This has happened before on another computer and the only fix I found was a restart, now it's starting on my main computer and is very annoying.  At first I thought it was just thunar, but even the command ls takes ten seconds to execute.  There is no spike in CPU or memory usage whenever I try to access my home directory so it shouldn't be a resource issue.  If I change directory, even to one in my home ls and thunar loads instantly.
Xubuntu 8.10 
2.8 GHz Intel Core 2 Duo
2GB RAM

---

### Post by Grant A. on 2009-01-22
What filesystem is your home directory using?

---

### Post by Crafty Kisses on 2009-01-22
Depending on your file system type, **ls** is reported to run very slow on NTFS mounted file systems, especially ones that have a lot of directories.

---

### Post by RedWagon on 2009-01-23
Found the problem.  I had a folder mounted to a share on my laptop that I forgot to unmount.

---

