---
title: "How to use grep in a script for a OR search?"
date: 2009-06-22
forum: General Help
---

### Post by SoftwareExplorer on 2009-06-22
hi.

Is there a way to use grep to return results that have 'this' or 'that'?

So if it has 

```
this
the
that
```

it would put out

```
this
that
```

---

### Post by Bachstelze on 2009-06-22
```
firas@iori ~ % cat test
this
the
that
firas@iori ~ % grep -E "(this|that)" test
this
that

```

---

### Post by SoftwareExplorer on 2009-06-22
Thanks. That worked.

---

