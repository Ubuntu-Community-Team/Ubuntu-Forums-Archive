---
title: "ntfs problem"
date: 2006-07-20
forum: Desktop Environments
---

### Post by ubun_nv on 2006-07-20
i can access ntfs partition.but everytime go to any folder in the ntfs partition it says "the folder contents could but displayed. sorry ,couldn't
 display all the contents of *. folder

please help

---

### Post by geco on 2006-07-20
how did you edit your fstab file?
from terminal:
```

cat /etc/fstab

```
Did your ntfs partition work well before?

---

### Post by ubun_nv on 2006-07-20
sudo gedit /etc/fstab

---

### Post by geco on 2006-07-20
> **geco said:**
> how did you edit your fstab file?
from terminal:
```

cat /etc/fstab

```
Did your ntfs partition work well before?

I'm sorry, I wanted to say "can you display your fstab file?"
To display it you cat do:
```

cat /etc/fstab

```

sorry again.

---

### Post by geco on 2006-07-20
> **aysiu said:**
> [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)


maybe this could help you.

---

