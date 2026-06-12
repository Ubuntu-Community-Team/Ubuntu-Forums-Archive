---
title: "[SOLVED] New user home directory"
date: 2009-01-05
forum: General Help
---

### Post by dbbolton on 2009-01-05
After some serious graphics trouble, I decided to do a clean install of ibex. I have a separate /home partition with data from the old system. The problem is that I need to create user accounts and set their home folders to the existing ones- e.g., create user "derek" and set ~ to the existing "/home/derek". I can't do this through the System > Admin > Users and Groups tool. Does anyone know how?

---

### Post by dbbolton on 2009-01-05
Ok, it's:

```

# useradd -d /home/derek derek

```

Then I set the user's password with:

```
# passwd derek
```

---

