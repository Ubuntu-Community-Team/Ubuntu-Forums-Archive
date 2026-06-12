---
title: "rsync ignores environmental variables"
date: 2009-03-16
forum: General Help
---

### Post by malfist on 2009-03-16
I have this in my rsync.conf
```

[backup]
    path = /home/$USER/backup
    use chroot = no
    monge symlinks = no
    uid = wendell
    gid = wendell
    read only = no
    list = yes
    auth users = wendell
    secrets file = /etc/rsyncd.secrets

```

But when I try to use rsync and authenticate with wendell (there is a /home/wendell/backup) it fails with 
@ERROR: chdir /home/$USER/backup failed
: No such file or directory (2)

Any idea how I can fix this?

---

