---
title: "Path to premounted ntfs disks"
date: 2006-07-15
forum: Desktop Environments
---

### Post by Epimetheus on 2006-07-15
What is the path to the disks that ubuntu mounts automagically when installed?

i know its usually /dev/hda1 and such but i cant seem to be able to access those as directories.

---

### Post by Ramses de Norre on 2006-07-15
No, things starting with /dev/ are device nodes, it are files that represent hardware. What you're looking for are the mountpoints. And I think you'll find them in /media/.

---

### Post by Epimetheus on 2006-07-15
Thanks alot for the fast reply!

---

### Post by randell6564 on 2006-07-15
You also need to make sure that they are mounted.  check your /etc/fstab

---

