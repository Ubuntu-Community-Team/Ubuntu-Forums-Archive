---
title: "change disk location in command line"
date: 2009-01-20
forum: General Help
---

### Post by miroslav_karpis on 2009-01-20
Hi All,
please how can I browse in command line between disks?
For example I have disks: C:, D: and E:
how I can go from C: to D:?

---

### Post by iaculallad on 2009-01-20
Basically, you could just do:

```
cd /media/drive_name
```

Or try listing the content of /media directory first:

```
ls /media
```

mounted partition could be located on /media directory.

---

### Post by miroslav_karpis on 2009-01-20
thanks ;)...
was trying the old dos commands...without success...

but now I know...

---

