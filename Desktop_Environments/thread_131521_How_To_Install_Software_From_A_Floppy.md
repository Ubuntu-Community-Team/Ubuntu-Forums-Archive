---
title: "How To Install Software From A Floppy?"
date: 2006-02-16
forum: Desktop Environments
---

### Post by AETrailblazer on 2006-02-16
Yes, I know this probably sounds asinine to most of the vets here, but I'm brand new to Linux and I'm wondering how to install .tar.gz files, in detail please, (Specifically The New DivX) onto Ubuntu. Any help would be greatly apprecitaed, Thanks!

---

### Post by maxomai on 2006-02-16
[LIST]
[*]Mount floppy: mount /dev/floppy /mnt/floppy  (or vice-versa)
[*]Copy tarball into your home directory (I have a ~/downloads directory just for storing such files). You might want to put the tarball in a directory of its own (e.g. ~/downloads/divx/)
[*]cd to tarball directory; run tar -zxvf whatever.tar.gz
[*]follow instructions in README. You may want to run some of those instructions via sudo.
[/LIST]

You might do better, though, to use a debian package if you can find it.

---

### Post by Lord Illidan on 2006-02-16
[quote=AETrailblazer]Yes, I know this probably sounds asinine to most of the vets here, but I'm brand new to Linux and I'm wondering how to install .tar.gz files, in detail please, (Specifically The New DivX) onto Ubuntu. Any help would be greatly apprecitaed, Thanks![/quote]

No questions are asinine in this forum :-D
One thing, though.. tar.gz files are actually compressed folders, similar to .zip.

Therefore, you don't install them, you extract them...

Welcome to the forums, seeing that it is your first post!

---

### Post by maxomai on 2006-02-17
[QUOTE=Lord Illidan]No questions are asinine in this forum :-D
One thing, though.. tar.gz files are actually compressed folders, similar to .zip.

Therefore, you don't install them, you extract them...

Welcome to the forums, seeing that it is your first post![/QUOTE]

Well, okay, but semantics aside, the old fashioned way for installing any new software for Linux has been to extract a gzipped tarball into a directory, run Make a bunch of times, hope everything works, and then eventually install the completed application and its sattelite of supporting files into /usr/something.

Compared to that mess, apt-get is a dream. Not a perfect dream, but much easier than tarballs.

---

