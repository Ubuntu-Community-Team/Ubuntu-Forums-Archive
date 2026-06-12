---
title: "disable CTRL-ALT-DEL in Lubuntu"
date: 2012-03-21
forum: Desktop Environments
---

### Post by cccc on 2012-03-21
Hi

How can I disable CTRL-ALT-DEL in Lubuntu?

---

### Post by SteveDee on 2012-03-23
> **cccc said:**
> Hi

How can I disable CTRL-ALT-DEL in Lubuntu?

<ctrl><alt><del> loads lxtask in Lubuntu due to the detail in /home/{user}/.config/openbox/lubuntu-rc.xml

I suggest you first make a copy of this file in case your edit goes bad (call it lubuntu-rc.org).

Now open /home/{user}/.config/openbox/lubuntu-rc.xml in your text editor and search for: lxtask

Now highlight and delete this section:-
```

<!-- Launch Task Manager with Ctrl+Alt+Del --><keybind key="A-C-Delete">
<action name="Execute"><command>lxtask</command></action></keybind>

```

Save changes, log-out of Lubuntu, then log back in and try <ctrl><alt><del>

---

### Post by cccc on 2012-03-23
Thx a lot, it works well now.

---

