---
title: "Any user can delete the windows host"
date: 2009-01-12
forum: General Help
---

### Post by luismi on 2009-01-12
Hello, any user can access /host mount point and delete the entire windows installation, /host is mounted with perms "777".

regards

---

### Post by brandon88tube on 2009-01-12
If you are worried about that just change the permissions on the folder.

---

### Post by cdtech on 2009-01-12
How do you have your /etc/fstab file setup?
```
/media/Vista ntfs defaults,**umask=007**,gid=46 0 0
```

---

### Post by luismi on 2009-01-12
> **brandon88tube said:**
> If you are worried about that just change the permissions on the folder.

You cant, a "chmod 770 /host" has no effect.

---

### Post by luismi on 2009-01-12
> **cdtech said:**
> How do you have your /etc/fstab file setup?
```
/media/Vista ntfs defaults,**umask=007**,gid=46 0 0
```

I have not touched fstab, there arent ntfs mounted partitions.

---

### Post by luismi on 2009-01-15
Please, can anyone confirm that on a stock ubuntu/wubi install any non privileged user can delete the entire system with an "rm -rf /hosts"?

Seems that no one cares...

---

### Post by brandon88tube on 2009-01-15
I don't know as I have never tried this, but if you feel its an issue then bring it to Ago's attention.

---

