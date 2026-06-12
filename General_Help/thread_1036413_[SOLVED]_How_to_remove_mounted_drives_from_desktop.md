---
title: "[SOLVED] How to remove mounted drives from desktop"
date: 2009-01-10
forum: General Help
---

### Post by Toady00 on 2009-01-10
I have a windows home server. The only way I have to access the shares are to mount each one indiviually. There are 8 shares on my home server so I'm mounting 8 times and each one starts cluttering up my desktop. I want to create a launcher that points to the directory where all the drives are mounted but I don't want the 8 mounts to show up on the desktop. Thanks for any help.

---

### Post by JECHO on 2009-01-10
> **Toady00 said:**
> I have a windows home server. The only way I have to access the shares are to mount each one indiviually. There are 8 shares on my home server so I'm mounting 8 times and each one starts cluttering up my desktop. I want to create a launcher that points to the directory where all the drives are mounted but I don't want the 8 mounts to show up on the desktop. Thanks for any help.


press alt+f2 and run:

```
gconf-editor
```

when the config editor pops up click apps > nautilus > desktop and uncheck volumes_visible 

whollah! :)

---

### Post by Toady00 on 2009-01-10
Thanks that worked.

---

### Post by blackened on 2009-01-12
> **Toady00 said:**
> Thanks that worked.
Please mark your threads as solved when your questions have been answered to your satisfaction.

**EDIT**: Excuse my rudeness, you did already.

---

### Post by deancasino on 2009-10-26
Fantastic, I LOVE this forum! seriously.

---

