---
title: "remove a existing user from an existing group"
date: 2009-01-04
forum: General Help
---

### Post by gypsumwolf on 2009-01-04
How do I remove a existing user from an existing group?

for example

```

bash~$groups tom
tom admin
bash~$ (something goes here)
bash~$groups tom
tom
bash~$
```

---

### Post by HalPomeranz on 2009-01-04
Well, you can edit /etc/group and remove the user from the group (or via the GUI under "System... Administration... Users & Groups).  But the user will have to log out and log back in again before they lose the group memberships in their existing shells.  There's no command for dropping group privileges once you have them.

---

### Post by gypsumwolf on 2009-01-04
Thats what I was looking for thanks.

---

