---
title: "rsync ???"
date: 2009-06-04
forum: General Help
---

### Post by colau on 2009-06-04
Hi,
If I use rsync -a then what would be the compression level?
Is this archive mode equivalent to tar?

How can I customize the compression level of rsync?

---

### Post by XCan on 2009-06-04
I don't think -a (archive mode) is the same as rsync would tar your backup. -a is equivalent to the flags -rlptgoD. The compression -z is only used during transfer to speed it up.

---

