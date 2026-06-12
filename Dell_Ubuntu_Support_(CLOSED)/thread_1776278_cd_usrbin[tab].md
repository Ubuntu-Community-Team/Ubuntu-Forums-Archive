---
title: "cd /usr/bin/[tab]"
date: 2011-06-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xtracool_protik on 2011-06-05
Ok so is it a feature/easter egg or a bug??

Trying to do cd /usr/bin/[tab] -- keep pressing and I get on terminal is:

 ```
wisemonkey@DevelopmentMachine:~$ cd /usr/bin/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/X11/

```

anyone else?

thanks

---

### Post by xtracool_protik on 2011-06-05
uname -a produces:

```
Linux DevelopmentMachine 2.6.39-020639rc5-generic #201105041556 SMP Wed May 4 15:59:47 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by papibe on 2011-06-05
It is indeed an odd behavior, but it is not a bug.

The first time X11/ appears is because it is the only directory available to expand. However, X11 is a link to /usr/bin so it keeps happening.

It is more of a 'questionable' design decision but not a bug.

Regards.

---

### Post by xtracool_protik on 2011-06-05
Now that u mention,
 I see X11 has a symlink to current folder itself and current folder contains X11 so its kind of an infinite loop.

 Why would that be?

---

