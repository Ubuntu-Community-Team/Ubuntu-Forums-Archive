---
title: "su problems"
date: 2009-02-16
forum: General Help
---

### Post by xGutsAndGloryx on 2009-02-16
i installed kubuntu 8.10. i tried to use the su command. it ask for my password. i entered the correct password but it says failed. what do i do?

---

### Post by snova on 2009-02-16
You cannot log in as root; use sudo instead.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Cl0ud9 on 2009-02-16
You can log in as root but it is not recommended. Google it to learn how to enable the root user in Ubuntu.

---

### Post by Phlee on 2009-02-16
> **Cl0ud9 said:**
> You can log in as root but it is not recommended. Google it to learn how to enable the root user in Ubuntu.

I useually just:

[[snip]]
Then you can su.
Although it's not a common practice;)

You can also:

```
sudo -s
```

---

