---
title: "Error with Add/Remove Applications"
date: 2008-12-22
forum: General Help
---

### Post by esmurdo on 2008-12-22
When I try to install a program, I receive the following error:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

When I try to run "sudo dpkg --configure -a", I then receive this error:
```
dpkg: failed to write status record about `python-beagle' to `/var/lib/dpkg/status': No space left on device
```

---

### Post by beno1990 on 2008-12-22
Open the system monitor and go to the filesystems tab, and report how much free space each of your filesystems has.

---

### Post by esmurdo on 2008-12-23
gvfs-fuse-daemon has 0 bytes out of 0 free
binfmt_misc has 0 bytes out of 0 free
overflow (/tmp) has 988KiB out of 1.0MiB free.

I have all filesystems selected, and that's all I see.

---

### Post by taurus on 2008-12-23
Applications -> Accessories -> Terminal
```
sudo apt-get clean
df -h
```

---

### Post by esmurdo on 2008-12-23
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get clean
df -h
```

Thank you!!!! Now can you tell me what that did exactly? i can understand the clean, but the df -h?

---

### Post by taurus on 2008-12-23
df -h will show you the current disk usage.

```
man df
```

---

### Post by snova on 2008-12-23
> **esmurdo said:**
> Thank you!!!! Now can you tell me what that did exactly? i can understand the clean, but the df -h?

df is a command to get information about used disk space. -h is an option to print it in more readable units- "Human readable".

---

