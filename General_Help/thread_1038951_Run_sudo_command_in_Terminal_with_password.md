---
title: "Run sudo command in Terminal with password"
date: 2009-01-14
forum: General Help
---

### Post by davico on 2009-01-14
Hallo I am trying to run Sudo command in the terminal and passing directly my password.

I tried some combinations but ^they do not work:

echo password | sudo -S command

sudo -S command < password

Does someone know? Thanks

---

### Post by iaculallad on 2009-01-14
That would be:

```
echo password | sudo -S command
```

Replace password with your own password.

HTH

---

