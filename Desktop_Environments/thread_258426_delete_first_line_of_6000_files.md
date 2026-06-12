---
title: "delete first line of 6000 files"
date: 2006-09-15
forum: Desktop Environments
---

### Post by harty83 on 2006-09-15
I need to delete just the first line in 6000 files.  How would I do that using a command in a terminal?  I'm assuming it would be something like "for i in *; do sed ...; done;"

Thanks!
Alan

---

### Post by lagagnon on 2006-09-15
sed -e '1 d' filenames

but if you have many files, yes, put them in a loop with the above command.

---

