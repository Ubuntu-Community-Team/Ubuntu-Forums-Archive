---
title: "How Do I Find a File's Location?"
date: 2009-01-03
forum: General Help
---

### Post by GuitarRocker2562 on 2009-01-03
Okay, lets say I want to open smb.conf, but I don't know where the file is. Is there a command that would tell me the location of the file?

---

### Post by jerome1232 on 2009-01-03
Well yes, but before we get into that smb.conf is a configuration file for samba, system wide configuration files are almost always in /etc.

As for locating files you can use the locate command!
```
locate smb.conf
```

Knowing a bit about how the file hiearchy works in linux helps to just "know" where a file ought to be. This might be a bit in-depth but a overview should give you an idea of where files go. [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html)

---

### Post by GuitarRocker2562 on 2009-01-03
Thanks. That actually makes sense, but you know how sometimes config files are in subfolders of /etc. But seriously, thanks a ton, I never would have though of trying locate, lol.

---

### Post by x1a4 on 2009-01-03
You can also use slocate, find or sfind.  If you want a GUI use Catfish,  GNOME-Search-Tool or kFind on KDE.  Just search through the repositories and you'll find a variety of file search utilities.

---

### Post by dagnabit dang doohickey on 2009-01-03
The [whereis]("http://linux.die.net/man/1/whereis") command.

If whereis doesn't give satisfactory results, use find:
```
find / -name "*filename*" 2>/dev/null
```

---

