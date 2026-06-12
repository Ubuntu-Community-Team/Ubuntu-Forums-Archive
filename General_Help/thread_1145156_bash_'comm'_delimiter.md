---
title: "bash 'comm' delimiter"
date: 2009-05-01
forum: General Help
---

### Post by prem1er on 2009-05-01
I'm comparing 2 files with 'comm' and the output results in a tab delimited file.  Is there any way to create a '|' (pipe) delimited file with 'comm'?  TIA

---

### Post by sisco311 on 2009-05-01
```
man comm
``` :evil:

```
comm --output-delimiter="|" ...
```

---

### Post by prem1er on 2009-05-01
> **sisco311 said:**
> ```
man comm
``` :evil:

```
comm --output-delimiter="|" ...
```

Sorry. Did not see that. Thank you.

---

### Post by sisco311 on 2009-05-01
You're welcome.

You can also replace the tabs with sed:
```
comm file1 file2 | sed "s/\t/\|/g"
```

sed "s/foo/bar/g" = replace (s) foo with bar; g = replace all instances in a line

---

