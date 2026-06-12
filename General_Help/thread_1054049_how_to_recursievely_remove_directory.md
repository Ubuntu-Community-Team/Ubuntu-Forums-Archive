---
title: "how to recursievely remove directory?"
date: 2009-01-29
forum: General Help
---

### Post by abhilashm86 on 2009-01-29
i tried normal rmdir command to delete a directory.
it always tells directory not empty,like this

[email]abhilash@abhi:~/.purple[/email]$ rmdir certificates
rmdir: failed to remove `certificates': Directory not empty

its so long time to delete these things,so i knew we can recursively delete directories,please tell how to do? i want to remove whole pidgin users files and others:)

---

### Post by sisco311 on 2009-01-29
```
rm -r path/to/dir
```

```
man rm
```

---

### Post by abhilashm86 on 2009-01-29
> **sisco311 said:**
> ```
rm -r path/to/dir
```

```
man rm
```

done thanks friend:)

i was in hurry,din't check man,ha ha,anyways job done

---

