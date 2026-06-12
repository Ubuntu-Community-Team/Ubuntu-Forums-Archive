---
title: "Package for Keyboard Configuration"
date: 2008-07-08
forum: Desktop Environments
---

### Post by pupeno on 2008-07-08
Hello,

Does anybody know which one is the package containing the keyboard configuration tool of Ubuntu?

Thanks.

---

### Post by sdennie on 2008-07-08
If you are referring to the application you get from System->Preferences->Keyboard:

```

$ dpkg -S /usr/bin/gnome-keyboard-properties
gnome-control-center: /usr/bin/gnome-keyboard-properties

```

So, package gnome-control-center has that tool.

---

### Post by pupeno on 2008-07-08
Thank you.:)

---

### Post by klikevil on 2011-06-22
> **sdennie said:**
> If you are referring to the application you get from System->Preferences->Keyboard:

```

$ dpkg -S /usr/bin/gnome-keyboard-properties
gnome-control-center: /usr/bin/gnome-keyboard-properties

```So, package gnome-control-center has that tool.


Thanks, you taught me something really useful.

---

