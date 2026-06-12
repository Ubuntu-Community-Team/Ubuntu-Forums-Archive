---
title: "Permanent partition permission changes?"
date: 2009-05-24
forum: Desktop Environments
---

### Post by natousayni on 2009-05-24
Hi!

I`m trying to set up permission changes for a volume. and at each reboot, the permissions com back to default... (ubuntu (9,04)

i`ve modifier /etc/fstab (this is stable):

```

/dev/sda4                                  /media/DADOS    vfat         rw,suid,dev,exec,auto,user,async                    0  0  

```

then modified device and mount point permissions (this change at every reboot to root):
```

sudo chown -R dia:dia /media/DADOS
sudo chown dia:dia /dev/sda4

```

then i mount the volume again and i normally manage to r x w on it.

but after a restart, the pernission com back to rootowner...

any ideas ?

on irc they told me to look around Alsa driver issues: i`ve attempt that:

```
sudo alsactl store
```

and that:

[http://alsa.opensrc.org/index.php/Using_alsactl_to_preserve_volume_state](http://alsa.opensrc.org/index.php/Using_alsactl_to_preserve_volume_state)

with no sucess...

so i set OSS sound drivers (realtech ALC883). still don`t work...


thx for reading! and any further help :)

++

---

### Post by merlinus on 2009-05-24
Can you set permissions on vfat volumes?

---

### Post by natousayni on 2009-05-24
sweet...

thanks merlin !


for the record, i had this to /etc/fstab :

```

/dev/sda4 /media/DADOS   vfat   uid=dia,gid=users,utf8=true 0 0

```

++

---

