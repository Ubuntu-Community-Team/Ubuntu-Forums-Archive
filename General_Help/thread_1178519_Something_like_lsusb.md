---
title: "Something like lsusb?"
date: 2009-06-04
forum: General Help
---

### Post by Jonnox on 2009-06-04
Does anyone know of a utility like ```
lsusb
``` but instead of showing bus informaition, it shows mounting information? Kind of like what is shown in ```
/dev/disk/by-id/
```

---

### Post by s.fox on 2009-06-04
Hi,

Do you mean something like:

```
cat /etc/fstab
```

Hope this helps,

-Ash R

---

### Post by Jonnox on 2009-06-04
no i need something that I can choose where to mount manually. So basically instead of trial and error mounting and unmount my sda* trying to find the right one, it would tell me which one is what.

Thanks though

---

### Post by merlinus on 2009-06-04
This may be useful:

```

mount

```

---

### Post by Jonnox on 2009-06-04
> **merlinus said:**
> This may be useful:

```

mount

```

The problem is that mount only displays currently mounted items, I was hoing something existed that showed both mounted and non-mounted

---

### Post by merlinus on 2009-06-04
If you run 

```

sudo mount -a

```it should mount all your partitions and drives, and then the mount command will list them.

/etc/fstab will let you see which are auto mounted on startup.

hth...

---

