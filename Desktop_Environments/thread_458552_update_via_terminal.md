---
title: "update via terminal?"
date: 2007-05-29
forum: Desktop Environments
---

### Post by maxwellcom on 2007-05-29
Is there a way to manually check for and install updates via the terminal (i.e., the equivalent to System>Administration>Update Manager)?

---

### Post by araz on 2007-05-29
This is one way
> sudo aptitude update&&sudo aptitude upgrade

---

### Post by mlind on 2007-05-30
what araz said, except invoke update before upgrade
```

sudo aptitude update
sudo aptitude upgrade

```

---

