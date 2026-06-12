---
title: "gnunet-qt gusty"
date: 2007-10-09
forum: Desktop Environments
---

### Post by rcmn on 2007-10-09
In Gusty testing.

I'm trying to use the gnunet-qt interface for Gnunet but the interface launch and i get the following error in the bottom bar.
```
 QLibrary::load_sys: Cannot load libgnunetqtmodule_stats (libgnunetqtmodule_stats.so cannot open shared object file: no such file or directory)

```

resolution:

```
sudo ln -s libgnunetqtmodule_stats.so.1.0.0 libgnunetqtmodule_stats.so
sudo ln -s libgnunetqtmodule_fs.so.1.0.0 libgnunetqtmodule_fs.so
sudo ln -s libgnunetqtmodule_general.so.1.0.0 libgnunetqtmodule_general.so
sudo ln -s libgnunetqtmodule_about.so.1.0.0 libgnunetqtmodule_about.so

```

---

