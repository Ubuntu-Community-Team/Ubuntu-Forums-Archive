---
title: "change filenames 20 files at once: script?"
date: 2006-02-01
forum: Desktop Environments
---

### Post by maxdevis on 2006-02-01
i have a lot of files where i want to change 1 character in the filename.
example
FN.M.01.ext
FN.M.02.ext
...

and i want to delete the .M of a lot of files.
is that possible or could someone write a script?

thanks

---

### Post by awi on 2006-02-01
```
$ man rename
```

---

### Post by kabus on 2006-02-01
```
for i in *; do n=`echo "$i" | sed "s/\.M//"`; mv "$i" "$n"; done
```

EDIT : or shorter

```
for i in *; do mv "$i" "${i/.M/}"; done
```

---

