---
title: "Mount multiple folders into one [Ubuntu SMB Server, Windows Client]"
date: 2014-07-16
forum: Desktop Environments
---

### Post by hashworks on 2014-07-16
I'm currently trying to mount my movie/tv folders in one folder so I can share it to windows clients using the smbd.

My first approach was:
```

cd /home/hashworks/Share/Series/; # Samba folder
find -type l -delete;
ln -s /media/hashworks/WDRED1/Series/* ./;
ln -s /media/hashworks/WDRED2/Series/* ./;
ln -s /media/hashworks/WDRED3/Series/* ./


cd /home/hashworks/Share/Movies/; # Samba folder
find -type l -delete;
ln -s /media/hashworks/WDRED4/Movies/* ./;
ln -s /media/hashworks/WDRED5/Movies/* ./

```

Which works on Linux and Windows Clients, but needs to be executed every 10 minutes to keep track of new folders - resulting in respinning 5 HDDs every 10min.


Another approach was using AUFS:
```

mount -t aufs -o br=/media/hashworks/WDRED4/Movies/=RW:/media/hashworks/WDRED5/Movies/=RW -o create=pmfs -o sum none /home/hashworks/Share/Movies/
mount -t aufs -o br=/media/hashworks/WDRED1/Series/=RW:/media/hashworks/WDRED2/Series/=RW:/media/hashworks/WDRED3/Series/=RW -o create=pmfs -o sum none /home/hashworks/Share/Series/

```

This solves the respin-problem and works fine when Linux Clients access the samba folder. Windows clients fail, through (something like "Wrong handler"). Same with unionfs-fuse.


Any ideas?

---

### Post by vanadium on 2014-07-16
Symbolic links may work only locally, and not when accessed over a share. Try to "mount bind" the directories. That way, they appear as physically mounted folders, and will exhibit no problem over a share.

---

### Post by hashworks on 2014-07-16
> **vanadium said:**
> Symbolic links may work only locally, and not when accessed over a share.

Symbolic links work in my whole local network without problems. This method will respin the HDD's every 10min, through.

---

### Post by vanadium on 2014-07-16
On closer inspection of your problem, mount bind will not be applicable. This allows to access only one directory from another location, whereas you want the contents of multiple directories to be accessible from a single location. I found a similar idea [here](http://www.kossboss.com/linux---virtually-merge-multiple-folders-with-symlinks-or-hardlinks-with-cp-command), but it is no better or worse than your approach.

---

