---
title: "Update problems"
date: 2009-02-01
forum: General Help
---

### Post by TaskmasterC on 2009-02-01
After installing Ultimate Edition 2 the system prompted me to do updates. I did. then the next day, it prompted me again. This time when I did them it went nuts. Now when I am booting up I have modules failing. If I try dpkg it says I have no privileges, yet I am the administrator. Please advise. I am still new to linux so any help is greatly appreciated

If you need any more info, let me know. Although you may have to tell me where and how to get it.


Thanks

---

### Post by braddcadd on 2009-02-03
try this first:
```

sudo aptitude update
sudo aptitude upgrade

```

try this next:
```

sudo dpkg ...

```

---

