---
title: "Need to copy locked files"
date: 2009-02-06
forum: General Help
---

### Post by kooldino on 2009-02-06
I'm currently running mediawiki and apache on a server, and need to move it to a new server.

Some of the files I need to copy over are in /usr/share/mediawiki1.10

However, some of the files in that directory are locked, so it won't allow me to tar or copy them.

So I'm guessing I either need to either:
-unlock them somehow
-force the copy somehow
-shutdown whatever service that is currently locking them.

Any input?

---

### Post by snova on 2009-02-06
Any files in /usr/share were most likely added by the package manager, copying them would not be wise. It'd be better just to install Mediawiki on the new server using Apt again.

Unless you're really sure you need to copy them for whatever reason... in which case, open Nautilus with root permissions. Press Alt-F2 and run:

```
gksudo nautilus
```

And be careful while you're at it.

---

### Post by SuperSonic4 on 2009-02-06
> **snova said:**
> Any files in /usr/share were most likely added by the package manager, copying them would not be wise. It'd be better just to install Mediawiki on the new server using Apt again.

Unless you're really sure you need to copy them for whatever reason... in which case, open Nautilus with root permissions. Press Alt-F2 and run:

```
gksudo nautilus
```

And be careful while you're at it.

Use sudo in terminal or kdesudo dolphin

You may need to install kdesudo first ```
sudo apt-get install kdesudo
``` and then ```
kdesudo dolphin
```

---

