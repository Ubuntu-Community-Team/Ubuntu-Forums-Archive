---
title: "I'm missing Administrations menu"
date: 2006-08-29
forum: Desktop Environments
---

### Post by pinokio on 2006-08-29
I've chmod my account to root group using Administrations menu in System->Administrations. So the next boot, when i logged in, the menu Administations just had the five items, the link of Synaptic Package Manager and Users Group was missed. I thought I must change the group of my account. But how to do this? How to view full items in the Administrations menu.
Thanks

---

### Post by mlind on 2006-08-29
> **pinokio said:**
> I've chmod my account to root group using Administrations menu in System->Administrations. So the next boot, when i logged in, the menu Administations just had the five items, the link of Synaptic Package Manager and Users Group was missed. I thought I must change the group of my account. But how to do this? How to view full items in the Administrations menu.
Thanks

I'm not sure what you mean by chmodding to root group, but open a terminal and type command
```

groups

```

Make sure you belong to following groups
```

adm dialout fax cdrom floppy tape audio dip video plugdev lpadmin scanner **admin**

```

You can add user to group using
```

sudo adduser *user* *group*

```

---

