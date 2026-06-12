---
title: "How to compare two folders?"
date: 2005-12-13
forum: Desktop Environments
---

### Post by maruchan on 2005-12-13
I would like to compare my Windows fonts folder with my .fonts folder in Linux. Is there an app somewhere that will let me do this? Thanks.

---

### Post by ow50 on 2005-12-13
diff for simple directory content comparison.
```
diff ~/.fonts /mnt/windows/WINDOWS/Fonts | sort
```

---

