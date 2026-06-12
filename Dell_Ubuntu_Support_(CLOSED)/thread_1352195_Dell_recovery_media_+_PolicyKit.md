---
title: "Dell recovery media + PolicyKit"
date: 2009-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by witeshark17 on 2009-12-11
The recovery media creator worked fine in 9.04. After the 9.10 upgrade, it's broken, reply from freedesktop.org bugzilla:

Not a D-Bus error. Your PolicyKit installation is either missing or invalid.
Please check with your distribution.

Is there a way to reestablish the protocol to what existed with 9.04?

---

### Post by witeshark17 on 2009-12-11
Is this the only case of the sort? Has anyone had any issues with freedesktop.org or PolicyKit ? Why is either in any way associated or involved with making a recovery DVD? :(

---

### Post by witeshark17 on 2009-12-12
Suggested fix:

```
sudo apt-get install --reinstall policykit policykit-gnome
```

Is this agreed to be a solution?

---

### Post by witeshark17 on 2009-12-17
Update: that reinstall worked. :guitar:

---

