---
title: "unable to use synaptic package manager"
date: 2009-05-02
forum: General Help
---

### Post by Heer2play on 2009-05-02
To change permission on folder I used gksudo nautilus. Now when I try to use it again nothing happens. Also synaptic package manager wont load. For both "Starting Administrative Application" appears on the bottom panel, and then nothing.

---

### Post by taurus on 2009-05-02
Do you remember which directory you changed the permissions?  Changing permissions or ownership of certain directories will trash your machine beyond repair.

---

### Post by Heer2play on 2009-05-02
yes, they were the etc folder.

---

### Post by taurus on 2009-05-02
> **Heer2play said:**
> yes, they were the **[COLOR="Red"]etc[/COLOR]** folder.

That is not a good thing to do.  Sudo will look in /etc/sudoers and if you have the permission for it, it will not run.

```
**[COLOR="Blue"]-r--r-----[/COLOR]** 1 root root 557 2009-04-28 15:04 /etc/sudoers
```

---

