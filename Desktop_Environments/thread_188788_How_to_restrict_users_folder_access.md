---
title: "How to restrict users folder access?"
date: 2006-06-04
forum: Desktop Environments
---

### Post by jonboy99 on 2006-06-04
Sorry about the noob question, but am setting up a multi user dapper system for my family, and want to restrict users from viewing other peoples files, ie only be able to see what is in their own home directory.
However they need to be able to use installed programs.

I feel a bit embarrassed at not being able to figure this one out on my own, but hey-ho..  :oops:

---

### Post by taurus on 2006-06-04
You can do that with (from a terminal, Applications -> Accessories -> Terminal),
```

sudo chmod 700 /home/username

```

---

