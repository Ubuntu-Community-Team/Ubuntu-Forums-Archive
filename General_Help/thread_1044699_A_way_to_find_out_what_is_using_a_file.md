---
title: "A way to find out what is using a file?"
date: 2009-01-19
forum: General Help
---

### Post by hardysummer on 2009-01-19
How do I find out which application is using a specific file?

Sometimes I want to unmount something only to be told that I can not unmount while the file is being used. How do I find out which application is using a certain file?

---

### Post by albinootje on 2009-01-19
> **hardysummer said:**
> How do I find out which application is using a specific file?

Sometimes I want to unmount something only to be told that I can not unmount while the file is being used. How do I find out which application is using a certain file?

You can try with "lsof", for example :
```

lsof | grep /media

```

---

