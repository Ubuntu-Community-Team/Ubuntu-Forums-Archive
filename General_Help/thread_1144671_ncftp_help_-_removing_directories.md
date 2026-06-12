---
title: "ncftp help - removing directories"
date: 2009-04-30
forum: General Help
---

### Post by Master_Odin on 2009-04-30
I just started using ftp/ncftp (gotta love the recursive put cmd!) and am trying to use them over a graphical interface (such as gFTP) just so I can get more comfortable in Terminal and because in the end, if you know what you're doing, it saves loads of time (typing is always faster then clicking :P).

Anyway, the one major problem I've encountered is not being able to remove any directories that aren't empty. I just can't figure out how to do it in ncftp. I tried:
```

rm -rf path/to/directory/

```
but got the following error: "delete path/to/directory/: remote rmdir failed."

I then tried:
```

rmdir /path/to/directory/

```
and that complained of it not being empty. Is there something obvious I'm missing here or must I go to gFTP for something so simple as deleting a non-empty directory? :confused:

---

### Post by Master_Odin on 2009-05-01
bump?

---

