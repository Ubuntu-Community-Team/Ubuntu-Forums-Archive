---
title: "xargs command"
date: 2009-04-01
forum: General Help
---

### Post by CJ1985 on 2009-04-01
Let's say 

```
... | xargs -n 1 echo | wc -l
```
Outputs 1560.

What would

```
 ... | xargs -n 20 echo | wc -l
```

output? I thought it was 1580 and I guess I'm wrong which is why I'm here to find out what I did wrong in selecting the answer I had.

---

