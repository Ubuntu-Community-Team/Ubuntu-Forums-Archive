---
title: "moving mountpoint"
date: 2009-04-02
forum: General Help
---

### Post by jon23d on 2009-04-02
I would like for /var/www to mount to sdc5, how can I change this?

Thanks

---

### Post by taurus on 2009-04-02
You should edit /etc/fstab

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add an entry in there for /dev/sdc5 that would look something like this.

```
/dev/sdc1   /var/www   ext3   defaults   0   2
```

---

### Post by jon23d on 2009-04-02
Thank you, just out of curiosity, is there a gui program that does this?

Thanks

---

