---
title: "When I use apt-get source, where does the source package go?"
date: 2005-10-16
forum: Desktop Environments
---

### Post by mostwanted on 2005-10-16
Thank you ;)

---

### Post by asimon on 2005-10-16
Four things will be put into the current directory (the one from which apt-get source is called):
1. A tarball with the original sources
2. A .dsc file with some package description
3. A compressed file with the debian/ubuntu specific patches
4. A directory with unpacked sources and the patches already applied.

For example:
```

# apt-get source imwheel
Reading package lists... Done
Building dependency tree... Done
Need to get 202kB of source archives.
Get:1 http://de.archive.ubuntu.com breezy/universe imwheel 1.0.0pre12-2 (dsc) [607B]
Get:2 http://de.archive.ubuntu.com breezy/universe imwheel 1.0.0pre12-2 (tar) [180kB]
Get:3 http://de.archive.ubuntu.com breezy/universe imwheel 1.0.0pre12-2 (diff) [21.6kB]
Fetched 202kB in 2s (95.5kB/s)
dpkg-source: extracting imwheel in imwheel-1.0.0pre12
dpkg-source: unpacking imwheel_1.0.0pre12.orig.tar.gz
dpkg-source: applying ./imwheel_1.0.0pre12-2.diff.gz


# ls -dF imwheel*
imwheel-1.0.0pre12/  imwheel_1.0.0pre12-2.diff.gz  imwheel_1.0.0pre12-2.dsc  imwheel_1.0.0pre12.orig.tar.gz

```

If you want to remove the source package again just delete those files and the dir.

---

### Post by logan77 on 2005-10-16
i think it's :

/var/cache/apt/archives/

(just quick "sudo find / -name *.deb" ) 
 ;)

---

