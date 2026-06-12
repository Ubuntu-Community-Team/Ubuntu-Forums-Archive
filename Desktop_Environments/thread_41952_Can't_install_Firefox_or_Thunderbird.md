---
title: "Can't install Firefox or Thunderbird"
date: 2005-06-15
forum: Desktop Environments
---

### Post by vtechstu on 2005-06-15
Hey, i've searched and can't find anything.  I follow the instructions to install, but i get this error.  How to i download this to that the install will work?

error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I'm using kubuntu, so i dont have Gnome.

Thanks.

---

### Post by SGC on 2005-06-15
Did you try this:

From:
kmenu > system > terminal program (Konsole)

Type the following:
```

sudo apt-get install mozilla-firefox mozilla-thunderbird

```

---

### Post by vtechstu on 2005-06-15
Thanks, that did the trick.  Thought i tried that, but guess not! Works pretty well now.

---

