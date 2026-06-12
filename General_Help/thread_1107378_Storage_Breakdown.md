---
title: "Storage Breakdown"
date: 2009-03-26
forum: General Help
---

### Post by verbal.kint on 2009-03-26
Isn't there a tool that will give you a breakdown of how much space is being used by each folder. Whats the name of it?

---

### Post by drs305 on 2009-03-26
You can use Disk Usage Analyzer (Accessories, Disk Usage Analzyer) or run the *du* command with the appropriate options. You can read about the options in "man du" but here is a sample command:
```
sudo du -h / --max-depth=2
```
the max depth switch tells it how many sublevels to descend
```

gksudo baobab  # Disk Usage Analzyer

```

---

### Post by verbal.kint on 2009-03-27
ya that was what i was thinking of, cheers

---

