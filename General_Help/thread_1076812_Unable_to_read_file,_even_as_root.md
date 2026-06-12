---
title: "Unable to read file, even as root"
date: 2009-02-21
forum: General Help
---

### Post by Ces on 2009-02-21
I have a file that I am unable to read (a few days ago it worked fine, and I cannot recall having done anything to cause this). The only thing I can think of, is that the file is placed in my ~/.private directory.

The file is a simple text file encoded in UTF-8.

I have tried to touch and chmod it, to no avail. I have even tried as root. A typical error is:

```
$ LANG=C sudo touch zzz
touch: cannot touch `zzz': Input/output error

$ LANG=C file zzz
zzz: writable, regular file, no read permission

$ ls -l zzz 
-rw-r--r-- 1 kess kess 2313 2009-02-19 22:45 zzz
```

Does someone know of a possible cause? Because I do not.

---

### Post by dcstar on 2009-02-21
> **Ces said:**
> I have a file that I am unable to read (a few days ago it worked fine, and I cannot recall having done anything to cause this). The only thing I can think of, is that the file is placed in my ~/.private directory.

The file is a simple text file encoded in UTF-8.

I have tried to touch and chmod it, to no avail. I have even tried as root. A typical error is:

```
$ LANG=C sudo touch zzz
touch: cannot touch `zzz': Input/output error

$ LANG=C file zzz
zzz: writable, regular file, no read permission

$ ls -l zzz 
-rw-r--r-- 1 kess kess 2313 2009-02-19 22:45 zzz
```

Does someone know of a possible cause? Because I do not.

What are the permissions of the folder it is in?

---

### Post by Ces on 2009-02-22
The directory permissions (note that other files in the same directory work fine):
```
$ ls -ld zzz
drwxr-xr-x 16 kess kess 4096 2009-02-22 04:41 zzz
```

---

