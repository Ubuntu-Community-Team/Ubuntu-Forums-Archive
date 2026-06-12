---
title: "gnome-open"
date: 2011-01-17
forum: Desktop Environments
---

### Post by CulleyS on 2011-01-17
Hello,

Working under Ubuntu 10.10, i386, Gnome 2.32.0  If I try either of the following commands using gnome-terminal, they work as expected... opening the current working directory in nautilus:

```
gnome-open .
xdg-open .
```

However, testing this under terminal emulators such as guake, tilda, terminator, I receive the following error message with either command above:

```
Couldn't get a file descriptor referring to the console
```

Oddly enough, on my Arch Linux machine, I don't have this problem with terminal emulators.  Only major difference I can see is on Arch, I'm using Gnome 2.32.1

Any ideas?

Thanks,
Culley

---

