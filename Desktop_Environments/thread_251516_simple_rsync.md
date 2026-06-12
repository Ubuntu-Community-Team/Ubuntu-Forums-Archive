---
title: "simple rsync?"
date: 2006-09-05
forum: Desktop Environments
---

### Post by pwrstick on 2006-09-05
Hello,

I want to use rsync to synchronize two directories.  Much like an incremental backup, I just want to copy files that have been altered and leave the rest the same.

BTW this is a one way thing really, I have a source disk and a backup disk, and I just need to keep refreshing the backup disk.

Thanks

---

### Post by tkjacobsen on 2006-09-05
I use rsync with these options:

rsync -arvuz /src/foo/ /dest/foo

this will copy the contents of /src/foo/ into /dest/foo

options:
a: archive mode (keep owner and permissions)
r: recurse into directories
v: increase verbosity
u: update only (don't overwrite newer files - if you have edited files in destination)
z: compress file data


more info can be found in 'man rsync'

---

### Post by aysiu on 2006-09-05
I use ```
rsync -av /source/folder /destination
``` This puts (and updates) a copy of folder in /destination to be /destination/folder.

I've found that it does a recursive backup even though I don't put the -r flag in there; I don't do update-only, as I never modify the destination files; and I have no need to compress the data, as my back-up drive is huge.

Use whatever options work for you, of course.

---

### Post by pwrstick on 2006-09-05
Thanks!

---

